<script lang="ts">
  import { faHardDrive } from "@fortawesome/free-solid-svg-icons";
  import { PanelHeader, StatItem } from "$lib/components";
  import { formatBytes, formatPercentage } from "$lib/utils";

  export let diskTotalBytes: number;
  export let diskUsedBytes: number;
  export let diskFreeBytes: number;

  $: diskUsagePercentage = (diskUsedBytes / diskTotalBytes) * 100;
</script>

<div class="stat-panel">
  <PanelHeader
    icon={faHardDrive}
    title="Storage"
    usageValue={formatPercentage(diskUsagePercentage)}
  />
  <div class="stats-content">
    <StatItem label="Total" value={formatBytes(diskTotalBytes)} />
    <StatItem label="Used" value={formatBytes(diskUsedBytes)} />
    <StatItem label="Free" value={formatBytes(diskFreeBytes)} />
  </div>
</div>

<style>
  .stat-panel {
    flex: 0.8;
    min-width: 125px;
    background-color: var(--mantle);
    border-radius: 6px;
    padding: 0.75rem;
    display: flex;
    flex-direction: column;
  }

  .stats-content {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
  }
</style>
