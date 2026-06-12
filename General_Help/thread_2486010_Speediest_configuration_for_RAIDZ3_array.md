---
title: "Speediest configuration for RAIDZ3 array?"
date: 2023-04-17
forum: General Help
---

### Post by papriak on 2023-04-17
Hello all.

I'm getting an average of 50MB/s to and from my RAIDZ3 pool, but I know  it can go faster.  I believe I saw it exceed 500MB/s in a previous  install.

What settings should I use to get maximum speed efficiency for eight 4TB drives in a single pool?


I ran "arc_summary", because I heard it may help.  The results are below:


```
ZFS Subsystem Report                            Mon Apr 17 18:56:16 2023
Linux 5.19.0-38-generic                                   2.1.5-1ubuntu6
Machine: server (x86_64)                                  2.1.5-1ubuntu6

ARC status:                                                      HEALTHY
        Memory throttle count:                                         0

ARC size (current):                                   100.1 %   15.6 GiB
        Target size (adaptive):                       100.0 %   15.6 GiB
        Min size (hard limit):                          6.2 %  999.4 MiB
        Max size (high water):                           16:1   15.6 GiB
        Most Frequently Used (MFU) cache size:        < 0.1 %  191.5 KiB
        Most Recently Used (MRU) cache size:          100.0 %    7.6 GiB
        Metadata cache size (hard limit):              75.0 %   11.7 GiB
        Metadata cache size (current):                 72.0 %    8.4 GiB
        Dnode cache size (hard limit):                 10.0 %    1.2 GiB
        Dnode cache size (current):                   < 0.1 %  385.6 KiB

ARC hash breakdown:
        Elements max:                                              27.3M
        Elements current:                              84.9 %      23.2M
        Collisions:                                                43.4M
        Chain max:                                                    23
        Chains:                                                     4.1M

ARC misc:
        Deleted:                                                   24.0M
        Mutex misses:                                               5.0k
        Eviction skips:                                             6.2k
        Eviction skips due to L2 writes:                               0
        L2 cached evictions:                                     0 Bytes
        L2 eligible evictions:                                  19.8 GiB
        L2 eligible MFU evictions:                      0.2 %   36.6 MiB
        L2 eligible MRU evictions:                     99.8 %   19.8 GiB
        L2 ineligible evictions:                                 3.1 MiB

ARC total accesses (hits + misses):                               148.8M
        Cache hit ratio:                               99.4 %     148.0M
        Cache miss ratio:                               0.6 %     855.4k
        Actual hit ratio (MFU + MRU hits):             99.4 %     148.0M
        Data demand efficiency:                        72.9 %     150.1k
        Data prefetch efficiency:                       2.1 %     103.1k

Cache hits by cache type:
        Most frequently used (MFU):                    96.2 %     142.4M
        Most recently used (MRU):                       3.8 %       5.6M
        Most frequently used (MFU) ghost:             < 0.1 %       6.7k
        Most recently used (MRU) ghost:                 0.1 %      76.2k

Cache hits by data type:
        Demand data:                                    0.1 %     109.4k
        Demand prefetch data:                         < 0.1 %       2.1k
        Demand metadata:                               99.9 %     147.9M
        Demand prefetch metadata:                     < 0.1 %        634

Cache misses by data type:
        Demand data:                                    4.8 %      40.7k
        Demand prefetch data:                          11.8 %     100.9k
        Demand metadata:                               83.4 %     713.5k
        Demand prefetch metadata:                     < 0.1 %        291

DMU prefetch efficiency:                                             333
        Hit ratio:                                     79.9 %        266
        Miss ratio:                                    20.1 %         67

L2ARC not detected, skipping section

Solaris Porting Layer (SPL):
        spl_hostid                                                     0
        spl_hostid_path                                      /etc/hostid
        spl_kmem_alloc_max                                       1048576
        spl_kmem_alloc_warn                                        65536
        spl_kmem_cache_kmem_threads                                    4
        spl_kmem_cache_magazine_size                                   0
        spl_kmem_cache_max_size                                       32
        spl_kmem_cache_obj_per_slab                                    8
        spl_kmem_cache_reclaim                                         0
        spl_kmem_cache_slab_limit                                  16384
        spl_max_show_tasks                                           512
        spl_panic_halt                                                 0
        spl_schedule_hrtimeout_slack_us                                0
        spl_taskq_kick                                                 0
        spl_taskq_thread_bind                                          0
        spl_taskq_thread_dynamic                                       1
        spl_taskq_thread_priority                                      1
        spl_taskq_thread_sequential                                    4

Tunables:
        dbuf_cache_hiwater_pct                                        10
        dbuf_cache_lowater_pct                                        10
        dbuf_cache_max_bytes                        18446744073709551615
        dbuf_cache_shift                                               5
        dbuf_metadata_cache_max_bytes               18446744073709551615
        dbuf_metadata_cache_shift                                      6
        dmu_object_alloc_chunk_shift                                   7
        dmu_prefetch_max                                       134217728
        ignore_hole_birth                                              1
        l2arc_feed_again                                               1
        l2arc_feed_min_ms                                            200
        l2arc_feed_secs                                                1
        l2arc_headroom                                                 2
        l2arc_headroom_boost                                         200
        l2arc_meta_percent                                            33
        l2arc_mfuonly                                                  0
        l2arc_noprefetch                                               1
        l2arc_norw                                                     0
        l2arc_rebuild_blocks_min_l2size                       1073741824
        l2arc_rebuild_enabled                                          1
        l2arc_trim_ahead                                               0
        l2arc_write_boost                                        8388608
        l2arc_write_max                                          8388608
        metaslab_aliquot                                         1048576
        metaslab_bias_enabled                                          1
        metaslab_debug_load                                            0
        metaslab_debug_unload                                          0
        metaslab_df_max_search                                  16777216
        metaslab_df_use_largest_segment                                0
        metaslab_force_ganging                                  16777217
        metaslab_fragmentation_factor_enabled                          1
        metaslab_lba_weighting_enabled                                 1
        metaslab_preload_enabled                                       1
        metaslab_unload_delay                                         32
        metaslab_unload_delay_ms                                  600000
        send_holes_without_birth_time                                  1
        spa_asize_inflation                                           24
        spa_config_path                             /etc/zfs/zpool.cache
        spa_load_print_vdev_tree                                       0
        spa_load_verify_data                                           1
        spa_load_verify_metadata                                       1
        spa_load_verify_shift                                          4
        spa_slop_shift                                                 5
        vdev_file_logical_ashift                                       9
        vdev_file_physical_ashift                                      9
        vdev_removal_max_span                                      32768
        vdev_validate_skip                                             0
        zap_iterate_prefetch                                           1
        zfetch_array_rd_sz                                       1048576
        zfetch_max_distance                                     67108864
        zfetch_max_idistance                                    67108864
        zfetch_max_sec_reap                                            2
        zfetch_max_streams                                             8
        zfetch_min_distance                                      4194304
        zfetch_min_sec_reap                                            1
        zfs_abd_scatter_enabled                                        1
        zfs_abd_scatter_max_order                                     10
        zfs_abd_scatter_min_size                                    1536
        zfs_admin_snapshot                                             0
        zfs_allow_redacted_dataset_mount                               0
        zfs_arc_average_blocksize                                   8192
        zfs_arc_dnode_limit                                            0
        zfs_arc_dnode_limit_percent                                   10
        zfs_arc_dnode_reduce_percent                                  10
        zfs_arc_evict_batch_limit                                     10
        zfs_arc_eviction_pct                                         200
        zfs_arc_grow_retry                                             0
        zfs_arc_lotsfree_percent                                      10
        zfs_arc_max                                                    0
        zfs_arc_meta_adjust_restarts                                4096
        zfs_arc_meta_limit                                             0
        zfs_arc_meta_limit_percent                                    75
        zfs_arc_meta_min                                               0
        zfs_arc_meta_prune                                         10000
        zfs_arc_meta_strategy                                          1
        zfs_arc_min                                                    0
        zfs_arc_min_prefetch_ms                                        0
        zfs_arc_min_prescient_prefetch_ms                              0
        zfs_arc_p_dampener_disable                                     1
        zfs_arc_p_min_shift                                            0
        zfs_arc_pc_percent                                             0
        zfs_arc_prune_task_threads                                     1
        zfs_arc_shrink_shift                                           0
        zfs_arc_shrinker_limit                                     10000
        zfs_arc_sys_free                                               0
        zfs_async_block_max_blocks                  18446744073709551615
        zfs_autoimport_disable                                         1
        zfs_checksum_events_per_second                                20
        zfs_commit_timeout_pct                                         5
        zfs_compressed_arc_enabled                                     1
        zfs_condense_indirect_commit_entry_delay_ms                    0
        zfs_condense_indirect_obsolete_pct                            25
        zfs_condense_indirect_vdevs_enable                             1
        zfs_condense_max_obsolete_bytes                       1073741824
        zfs_condense_min_mapping_bytes                            131072
        zfs_dbgmsg_enable                                              1
        zfs_dbgmsg_maxsize                                       4194304
        zfs_dbuf_state_index                                           0
        zfs_ddt_data_is_special                                        1
        zfs_deadman_checktime_ms                                   60000
        zfs_deadman_enabled                                            1
        zfs_deadman_failmode                                        wait
        zfs_deadman_synctime_ms                                   600000
        zfs_deadman_ziotime_ms                                    300000
        zfs_dedup_prefetch                                             0
        zfs_delay_min_dirty_percent                                   60
        zfs_delay_scale                                           500000
        zfs_delete_blocks                                          20480
        zfs_dirty_data_max                                    3353453363
        zfs_dirty_data_max_max                                4294967296
        zfs_dirty_data_max_max_percent                                25
        zfs_dirty_data_max_percent                                    10
        zfs_dirty_data_sync_percent                                   20
        zfs_disable_ivset_guid_check                                   0
        zfs_dmu_offset_next_sync                                       1
        zfs_embedded_slog_min_ms                                      64
        zfs_expire_snapshot                                          300
        zfs_fallocate_reserve_percent                                110
        zfs_flags                                                      0
        zfs_free_bpobj_enabled                                         1
        zfs_free_leak_on_eio                                           0
        zfs_free_min_time_ms                                        1000
        zfs_history_output_max                                   1048576
        zfs_immediate_write_sz                                     32768
        zfs_initialize_chunk_size                                1048576
        zfs_initialize_value                        16045690984833335022
        zfs_keep_log_spacemaps_at_export                               0
        zfs_key_max_salt_uses                                  400000000
        zfs_livelist_condense_new_alloc                                0
        zfs_livelist_condense_sync_cancel                              0
        zfs_livelist_condense_sync_pause                               0
        zfs_livelist_condense_zthr_cancel                              0
        zfs_livelist_condense_zthr_pause                               0
        zfs_livelist_max_entries                                  500000
        zfs_livelist_min_percent_shared                               75
        zfs_lua_max_instrlimit                                 100000000
        zfs_lua_max_memlimit                                   104857600
        zfs_max_async_dedup_frees                                 100000
        zfs_max_log_walking                                            5
        zfs_max_logsm_summary_length                                  10
        zfs_max_missing_tvds                                           0
        zfs_max_nvlist_src_size                                        0
        zfs_max_recordsize                                       1048576
        zfs_metaslab_find_max_tries                                  100
        zfs_metaslab_fragmentation_threshold                          70
        zfs_metaslab_max_size_cache_sec                             3600
        zfs_metaslab_mem_limit                                        25
        zfs_metaslab_segment_weight_enabled                            1
        zfs_metaslab_switch_threshold                                  2
        zfs_metaslab_try_hard_before_gang                              0
        zfs_mg_fragmentation_threshold                                95
        zfs_mg_noalloc_threshold                                       0
        zfs_min_metaslabs_to_flush                                     1
        zfs_multihost_fail_intervals                                  10
        zfs_multihost_history                                          0
        zfs_multihost_import_intervals                                20
        zfs_multihost_interval                                      1000
        zfs_multilist_num_sublists                                     0
        zfs_no_scrub_io                                                0
        zfs_no_scrub_prefetch                                          0
        zfs_nocacheflush                                               0
        zfs_nopwrite_enabled                                           1
        zfs_object_mutex_size                                         64
        zfs_obsolete_min_time_ms                                     500
        zfs_override_estimate_recordsize                               0
        zfs_pd_bytes_max                                        52428800
        zfs_per_txg_dirty_frees_percent                                5
        zfs_prefetch_disable                                           0
        zfs_read_history                                               0
        zfs_read_history_hits                                          0
        zfs_rebuild_max_segment                                  1048576
        zfs_rebuild_scrub_enabled                                      1
        zfs_rebuild_vdev_limit                                  33554432
        zfs_reconstruct_indirect_combinations_max                   4096
        zfs_recover                                                    0
        zfs_recv_queue_ff                                             20
        zfs_recv_queue_length                                   16777216
        zfs_recv_write_batch_size                                1048576
        zfs_removal_ignore_errors                                      0
        zfs_removal_suspend_progress                                   0
        zfs_remove_max_segment                                  16777216
        zfs_resilver_disable_defer                                     0
        zfs_resilver_min_time_ms                                    3000
        zfs_scan_blkstats                                              0
        zfs_scan_checkpoint_intval                                  7200
        zfs_scan_fill_weight                                           3
        zfs_scan_ignore_errors                                         0
        zfs_scan_issue_strategy                                        0
        zfs_scan_legacy                                                0
        zfs_scan_max_ext_gap                                     2097152
        zfs_scan_mem_lim_fact                                         20
        zfs_scan_mem_lim_soft_fact                                    20
        zfs_scan_strict_mem_lim                                        0
        zfs_scan_suspend_progress                                      0
        zfs_scan_vdev_limit                                      4194304
        zfs_scrub_min_time_ms                                       1000
        zfs_send_corrupt_data                                          0
        zfs_send_no_prefetch_queue_ff                                 20
        zfs_send_no_prefetch_queue_length                        1048576
        zfs_send_queue_ff                                             20
        zfs_send_queue_length                                   16777216
        zfs_send_unmodified_spill_blocks                               1
        zfs_slow_io_events_per_second                                 20
        zfs_spa_discard_memory_limit                            16777216
        zfs_special_class_metadata_reserve_pct                        25
        zfs_sync_pass_deferred_free                                    2
        zfs_sync_pass_dont_compress                                    8
        zfs_sync_pass_rewrite                                          2
        zfs_sync_taskq_batch_pct                                      75
        zfs_traverse_indirect_prefetch_limit                          32
        zfs_trim_extent_bytes_max                              134217728
        zfs_trim_extent_bytes_min                                  32768
        zfs_trim_metaslab_skip                                         0
        zfs_trim_queue_limit                                          10
        zfs_trim_txg_batch                                            32
        zfs_txg_history                                              100
        zfs_txg_timeout                                                5
        zfs_unflushed_log_block_max                               131072
        zfs_unflushed_log_block_min                                 1000
        zfs_unflushed_log_block_pct                                  400
        zfs_unflushed_log_txg_max                                   1000
        zfs_unflushed_max_mem_amt                             1073741824
        zfs_unflushed_max_mem_ppm                                   1000
        zfs_unlink_suspend_progress                                    0
        zfs_user_indirect_is_special                                   1
        zfs_vdev_aggregate_trim                                        0
        zfs_vdev_aggregation_limit                               1048576
        zfs_vdev_aggregation_limit_non_rotating                   131072
        zfs_vdev_async_read_max_active                                 3
        zfs_vdev_async_read_min_active                                 1
        zfs_vdev_async_write_active_max_dirty_percent                 60
        zfs_vdev_async_write_active_min_dirty_percent                 30
        zfs_vdev_async_write_max_active                               10
        zfs_vdev_async_write_min_active                                2
        zfs_vdev_cache_bshift                                         16
        zfs_vdev_cache_max                                         16384
        zfs_vdev_cache_size                                            0
        zfs_vdev_default_ms_count                                    200
        zfs_vdev_default_ms_shift                                     29
        zfs_vdev_initializing_max_active                               1
        zfs_vdev_initializing_min_active                               1
        zfs_vdev_max_active                                         1000
        zfs_vdev_max_auto_ashift                                      16
        zfs_vdev_min_auto_ashift                                       9
        zfs_vdev_min_ms_count                                         16
        zfs_vdev_mirror_non_rotating_inc                               0
        zfs_vdev_mirror_non_rotating_seek_inc                          1
        zfs_vdev_mirror_rotating_inc                                   0
        zfs_vdev_mirror_rotating_seek_inc                              5
        zfs_vdev_mirror_rotating_seek_offset                     1048576
        zfs_vdev_ms_count_limit                                   131072
        zfs_vdev_nia_credit                                            5
        zfs_vdev_nia_delay                                             5
        zfs_vdev_queue_depth_pct                                    1000
        zfs_vdev_raidz_impl cycle [fastest] original scalar sse2 ssse3 avx2
        zfs_vdev_read_gap_limit                                    32768
        zfs_vdev_rebuild_max_active                                    3
        zfs_vdev_rebuild_min_active                                    1
        zfs_vdev_removal_max_active                                    2
        zfs_vdev_removal_min_active                                    1
        zfs_vdev_scheduler                                        unused
        zfs_vdev_scrub_max_active                                      3
        zfs_vdev_scrub_min_active                                      1
        zfs_vdev_sync_read_max_active                                 10
        zfs_vdev_sync_read_min_active                                 10
        zfs_vdev_sync_write_max_active                                10
        zfs_vdev_sync_write_min_active                                10
        zfs_vdev_trim_max_active                                       2
        zfs_vdev_trim_min_active                                       1
        zfs_vdev_write_gap_limit                                    4096
        zfs_vnops_read_chunk_size                                1048576
        zfs_zevent_len_max                                           512
        zfs_zevent_retain_expire_secs                                900
        zfs_zevent_retain_max                                       2000
        zfs_zil_clean_taskq_maxalloc                             1048576
        zfs_zil_clean_taskq_minalloc                                1024
        zfs_zil_clean_taskq_nthr_pct                                 100
        zil_maxblocksize                                          131072
        zil_nocacheflush                                               0
        zil_replay_disable                                             0
        zil_slog_bulk                                             786432
        zio_deadman_log_all                                            0
        zio_dva_throttle_enabled                                       1
        zio_requeue_io_start_cut_in_line                               1
        zio_slow_io_ms                                             30000
        zio_taskq_batch_pct                                           80
        zio_taskq_batch_tpq                                            0
        zvol_inhibit_dev                                               0
        zvol_major                                                   230
        zvol_max_discard_blocks                                    16384
        zvol_prefetch_bytes                                       131072
        zvol_request_sync                                              0
        zvol_threads                                                  32
        zvol_volmode                                                   1

VDEV cache disabled, skipping section

ZIL committed transactions:                                            0
        Commit requests:                                               0
        Flushes to stable storage:                                     0
        Transactions to SLOG storage pool:            0 Bytes          0
        Transactions to non-SLOG storage pool:        0 Bytes          0
```

---

### Post by MAFoElffen on 2023-04-18
Please go back to Post #1 and surround your raw output with CODE Tags. Use Advance Edit > Select the output > Select the "#" Icon to wrap what is highlighted with CODE Tags.

Assumptions- You are concerned about performance, so that brings up that is may be a server, with some kind of file service or database service...

What are the drives? (So that spec's can be looked up)
Is the drive sector size 512 bytes or 4 KiB? Is that consistent of all the drives?
What are the machines jobs? <services>
What is the size of the working dataset? (You stated the max size, which you would set 80% capacity as your soft limit.)
Besides it's main job, what other services are running?
How many clients and what are they?
How are you bench-marking it's performance? Just making sure the bench-marking is realistic/comparable to the service it is supposed to be providing.

Typically, I see about 200-300MB/s performance on RAIDZ3. It is the safest of RAIDZ types, but it's safety comes at a cost.

Pool performance tuning is a balance of ARC cache and network tuning. If you want to offload some of the bandwidth of the cache, then you would install an 512GB SSD for use as L2ARC. The network tweaks include the server and main clients.

Caching assumes that you reread something, so the reread is faster than having to read something for the first time. This helps with database services and file services, to a limit. The limit being that if the fie size is larger than the cache, then the cache is filled up, and performance falls off. For example, copying a 20GB file, versus 20 files of 1GB each.

Tuning the networking affects the throughput and bandwidth of what is possible in the connections between the server and the clients.

---

### Post by papriak on 2023-04-18
> **MAFoElffen said:**
> Please go back to Post #1 and surround your raw output with CODE Tags. Use Advance Edit > Select the output > Select the "#" Icon to wrap what is highlighted with CODE Tags.

Done, thanks.

> Assumptions- You are concerned about performance, so that brings up that is may be a server, with some kind of file service or database service...

Yes, it's a custom-built NAS on my home network. 

> What are the drives? (So that spec's can be looked up)
Is the drive sector size 512 bytes or 4 KiB? Is that consistent of all the drives?

All 8 drives are HGST HUS724040ALA640, revision MFAOAA70

[https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/data-center-drives/ultrastar-sata-series/data-sheet-ultrastar-7k4000.pdf](https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/data-center-drives/ultrastar-sata-series/data-sheet-ultrastar-7k4000.pdf)

> What are the machines jobs? <services>

Hosting the ZFS pool as a samba share.

> What is the size of the working dataset? (You stated the max size, which you would set 80% capacity as your soft limit.)

I don't recall setting a limit, might not be a bad idea to do so.


>  Besides it's main job, what other services are running? 

I remote-in using Cockpit, other than that it should just be Ubuntu's default services for the minimal Desktop 20.04 LTS version.

> How many clients and what are they?

Maximum of 3 Windows machines at a time.

> How are you bench-marking it's performance? Just making sure the bench-marking is realistic/comparable to the service it is supposed to be providing.

Transferring a single large file from a NVME SSD in the server to the pool, then back.  The server is headless so I'm monitoring the progress from Windows 10's file transfer histograms.

>  Typically, I see about 200-300MB/s performance on RAIDZ3. It is the safest of RAIDZ types, but it's safety comes at a cost.

Pool performance tuning is a balance of ARC cache and network tuning. If you want to offload some of the bandwidth of the cache, then you would install an 512GB SSD for use as L2ARC. The network tweaks include the server and main clients.

Caching assumes that you reread something, so the reread is faster than having to read something for the first time. This helps with database services and file services, to a limit. The limit being that if the fie size is larger than the cache, then the cache is filled up, and performance falls off. For example, copying a 20GB file, versus 20 files of 1GB each.

Tuning the networking affects the throughput and bandwidth of what is possible in the connections between the server and the clients.

I'd love to see transfer speeds go at least that high.  I should have a spare SSD laying around that I can install.

As for networking, my main Windows PC and the server both have 10GB NICs installed, connected to a switch with two 10G ports and eight 1G ports for the rest of the network.

---

### Post by #&amp;thj^% on 2023-04-18
> **MAFoElffen said:**
> 
Typically, I see about 200-300MB/s performance on RAIDZ3. It is the safest of RAIDZ types, but it's safety comes at a cost.

Pool performance tuning is a balance of ARC cache and network tuning. If you want to offload some of the bandwidth of the cache, then you would install an 512GB SSD for use as L2ARC. The network tweaks include the server and main clients.

Caching assumes that you reread something, so the reread is faster than having to read something for the first time. This helps with database services and file services, to a limit. The limit being that if the fie size is larger than the cache, then the cache is filled up, and performance falls off. For example, copying a 20GB file, versus 20 files of 1GB each.

Tuning the networking affects the throughput and bandwidth of what is possible in the connections between the server and the clients.
+1 My needs are simple and I follow this to the letter"K.I.S.S"
One pool is on nvme0n1p1 SSD about 40% used, I get 500-600 Mbs transfer rate speed, another spinning drive i get 55-65 MB speed and the Drive is 80% full
I agree with MAFoElffen on the installing a 512GB SSD for use as L2ARC. (It still won't be a speedster but will improve speed some)
```
------------------------------------------------------------------------
ZFS Subsystem Report                            Tue Apr 18 09:46:07 2023
Linux 6.2.0-20-generic                                    2.1.9-2ubuntu1
Machine: me-Lenovo-Legion-5-15ARH05 (x86_64)              2.1.9-2ubuntu1

ARC status:                                                      HEALTHY
        Memory throttle count:                                         0

ARC size (current):                                    99.7 %    3.8 GiB
        Target size (adaptive):                       100.0 %    3.8 GiB
        Min size (hard limit):                          6.2 %  243.5 MiB
        Max size (high water):                           16:1    3.8 GiB
        Most Frequently Used (MFU) cache size:          9.2 %  351.3 MiB
        Most Recently Used (MRU) cache size:           90.8 %    3.4 GiB
        Metadata cache size (hard limit):              75.0 %    2.9 GiB
        Metadata cache size (current):                 12.3 %  358.2 MiB
        Dnode cache size (hard limit):                 10.0 %  292.2 MiB
        Dnode cache size (current):                     7.5 %   21.8 MiB

ARC hash breakdown:
        Elements max:                                              55.6k
        Elements current:                              89.2 %      49.7k
        Collisions:                                                 4.7k
        Chain max:                                                     3
        Chains:                                                     1.1k

ARC misc:
        Deleted:                                                   68.7k
        Mutex misses:                                                 28
        Eviction skips:                                            79.6k
        Eviction skips due to L2 writes:                               0
        L2 cached evictions:                                     0 Bytes
        L2 eligible evictions:                                   3.1 GiB
        L2 eligible MFU evictions:                     18.8 %  597.8 MiB
        L2 eligible MRU evictions:                     81.2 %    2.5 GiB
        L2 ineligible evictions:                                 5.4 GiB

ARC total accesses (hits + misses):                                 1.8M
        Cache hit ratio:                               95.9 %       1.7M
        Cache miss ratio:                               4.1 %      73.5k
        Actual hit ratio (MFU + MRU hits):             94.3 %       1.7M
        Data demand efficiency:                        95.4 %     359.1k
        Data prefetch efficiency:                       0.3 %      45.4k

Cache hits by cache type:
        Most frequently used (MFU):                    75.2 %       1.3M
        Most recently used (MRU):                      23.1 %     397.9k
        Most frequently used (MFU) ghost:             < 0.1 %         52
        Most recently used (MRU) ghost:               < 0.1 %        302
        Anonymously used:                               1.6 %      27.8k

Cache hits by data type:
        Demand data:                                   19.9 %     342.6k
        Prefetch data:                                < 0.1 %        126
        Demand metadata:                               78.4 %       1.3M
        Prefetch metadata:                              1.6 %      28.2k

Cache misses by data type:
        Demand data:                                   22.5 %      16.6k
        Prefetch data:                                 61.7 %      45.3k
        Demand metadata:                               12.1 %       8.9k
        Prefetch metadata:                              3.7 %       2.7k

DMU prefetch efficiency:                                          149.8k
        Hit ratio:                                     36.6 %      54.9k
        Miss ratio:                                    63.4 %      94.9k

L2ARC not detected, skipping section

Solaris Porting Layer (SPL):
        spl_hostid                                                     0
        spl_hostid_path                                      /etc/hostid
        spl_kmem_alloc_max                                       1048576
        spl_kmem_alloc_warn                                        65536
        spl_kmem_cache_kmem_threads                                    4
        spl_kmem_cache_magazine_size                                   0
        spl_kmem_cache_max_size                                       32
        spl_kmem_cache_obj_per_slab                                    8
        spl_kmem_cache_reclaim                                         0
        spl_kmem_cache_slab_limit                                  16384
        spl_max_show_tasks                                           512
        spl_panic_halt                                                 0
        spl_schedule_hrtimeout_slack_us                                0
        spl_taskq_kick                                                 0
        spl_taskq_thread_bind                                          0
        spl_taskq_thread_dynamic                                       1
        spl_taskq_thread_priority                                      1
        spl_taskq_thread_sequential                                    4

Tunables:
        dbuf_cache_hiwater_pct                                        10
        dbuf_cache_lowater_pct                                        10
        dbuf_cache_max_bytes                        18446744073709551615
        dbuf_cache_shift                                               5
        dbuf_metadata_cache_max_bytes               18446744073709551615
        dbuf_metadata_cache_shift                                      6
        dmu_object_alloc_chunk_shift                                   7
        dmu_prefetch_max                                       134217728
        ignore_hole_birth                                              1
        l2arc_exclude_special                                          0
        l2arc_feed_again                                               1
        l2arc_feed_min_ms                                            200
        l2arc_feed_secs                                                1
        l2arc_headroom                                                 2
        l2arc_headroom_boost                                         200
        l2arc_meta_percent                                            33
        l2arc_mfuonly                                                  0
        l2arc_noprefetch                                               1
        l2arc_norw                                                     0
        l2arc_rebuild_blocks_min_l2size                       1073741824
        l2arc_rebuild_enabled                                          1
        l2arc_trim_ahead                                               0
        l2arc_write_boost                                        8388608
        l2arc_write_max                                          8388608
        metaslab_aliquot                                         1048576
        metaslab_bias_enabled                                          1
        metaslab_debug_load                                            0
        metaslab_debug_unload                                          0
        metaslab_df_max_search                                  16777216
        metaslab_df_use_largest_segment                                0
        metaslab_force_ganging                                  16777217
        metaslab_fragmentation_factor_enabled                          1
        metaslab_lba_weighting_enabled                                 1
        metaslab_preload_enabled                                       1
        metaslab_unload_delay                                         32
        metaslab_unload_delay_ms                                  600000
        send_holes_without_birth_time                                  1
        spa_asize_inflation                                           24
        spa_config_path                             /etc/zfs/zpool.cache
        spa_load_print_vdev_tree                                       0
        spa_load_verify_data                                           1
        spa_load_verify_metadata                                       1
        spa_load_verify_shift                                          4
        spa_slop_shift                                                 5
        vdev_file_logical_ashift                                       9
        vdev_file_physical_ashift                                      9
        vdev_removal_max_span                                      32768
        vdev_validate_skip                                             0
        zap_iterate_prefetch                                           1
        zfetch_array_rd_sz                                       1048576
        zfetch_max_distance                                     67108864
        zfetch_max_idistance                                    67108864
        zfetch_max_sec_reap                                            2
        zfetch_max_streams                                             8
        zfetch_min_distance                                      4194304
        zfetch_min_sec_reap                                            1
        zfs_abd_scatter_enabled                                        1
        zfs_abd_scatter_max_order                                     10
        zfs_abd_scatter_min_size                                    1536
        zfs_admin_snapshot                                             0
        zfs_allow_redacted_dataset_mount                               0
        zfs_arc_average_blocksize                                   8192
        zfs_arc_dnode_limit                                            0
        zfs_arc_dnode_limit_percent                                   10
        zfs_arc_dnode_reduce_percent                                  10
        zfs_arc_evict_batch_limit                                     10
        zfs_arc_eviction_pct                                         200
        zfs_arc_grow_retry                                             0
        zfs_arc_lotsfree_percent                                      10
        zfs_arc_max                                                    0
        zfs_arc_meta_adjust_restarts                                4096
        zfs_arc_meta_limit                                             0
        zfs_arc_meta_limit_percent                                    75
        zfs_arc_meta_min                                               0
        zfs_arc_meta_prune                                         10000
        zfs_arc_meta_strategy                                          1
        zfs_arc_min                                                    0
        zfs_arc_min_prefetch_ms                                        0
        zfs_arc_min_prescient_prefetch_ms                              0
        zfs_arc_p_dampener_disable                                     1
        zfs_arc_p_min_shift                                            0
        zfs_arc_pc_percent                                             0
        zfs_arc_prune_task_threads                                     1
        zfs_arc_shrink_shift                                           0
        zfs_arc_shrinker_limit                                     10000
        zfs_arc_sys_free                                               0
        zfs_async_block_max_blocks                  18446744073709551615
        zfs_autoimport_disable                                         1
        zfs_btree_verify_intensity                                     0
        zfs_checksum_events_per_second                                20
        zfs_commit_timeout_pct                                         5
        zfs_compressed_arc_enabled                                     1
        zfs_condense_indirect_commit_entry_delay_ms                    0
        zfs_condense_indirect_obsolete_pct                            25
        zfs_condense_indirect_vdevs_enable                             1
        zfs_condense_max_obsolete_bytes                       1073741824
        zfs_condense_min_mapping_bytes                            131072
        zfs_dbgmsg_enable                                              1
        zfs_dbgmsg_maxsize                                       4194304
        zfs_dbuf_state_index                                           0
        zfs_ddt_data_is_special                                        1
        zfs_deadman_checktime_ms                                   60000
        zfs_deadman_enabled                                            1
        zfs_deadman_failmode                                        wait
        zfs_deadman_synctime_ms                                   600000
        zfs_deadman_ziotime_ms                                    300000
        zfs_dedup_prefetch                                             0
        zfs_delay_min_dirty_percent                                   60
        zfs_delay_scale                                           500000
        zfs_delete_blocks                                          20480
        zfs_dirty_data_max                                     817150771
        zfs_dirty_data_max_max                                2042876928
        zfs_dirty_data_max_max_percent                                25
        zfs_dirty_data_max_percent                                    10
        zfs_dirty_data_sync_percent                                   20
        zfs_disable_ivset_guid_check                                   0
        zfs_dmu_offset_next_sync                                       1
        zfs_embedded_slog_min_ms                                      64
        zfs_expire_snapshot                                          300
        zfs_fallocate_reserve_percent                                110
        zfs_flags                                                      0
        zfs_free_bpobj_enabled                                         1
        zfs_free_leak_on_eio                                           0
        zfs_free_min_time_ms                                        1000
        zfs_history_output_max                                   1048576
        zfs_immediate_write_sz                                     32768
        zfs_initialize_chunk_size                                1048576
        zfs_initialize_value                        16045690984833335022
        zfs_keep_log_spacemaps_at_export                               0
        zfs_key_max_salt_uses                                  400000000
        zfs_livelist_condense_new_alloc                                0
        zfs_livelist_condense_sync_cancel                              0
        zfs_livelist_condense_sync_pause                               0
        zfs_livelist_condense_zthr_cancel                              0
        zfs_livelist_condense_zthr_pause                               0
        zfs_livelist_max_entries                                  500000
        zfs_livelist_min_percent_shared                               75
        zfs_lua_max_instrlimit                                 100000000
        zfs_lua_max_memlimit                                   104857600
        zfs_max_async_dedup_frees                                 100000
        zfs_max_log_walking                                            5
        zfs_max_logsm_summary_length                                  10
        zfs_max_missing_tvds                                           0
        zfs_max_nvlist_src_size                                        0
        zfs_max_recordsize                                       1048576
        zfs_metaslab_find_max_tries                                  100
        zfs_metaslab_fragmentation_threshold                          70
        zfs_metaslab_max_size_cache_sec                             3600
        zfs_metaslab_mem_limit                                        25
        zfs_metaslab_segment_weight_enabled                            1
        zfs_metaslab_switch_threshold                                  2
        zfs_metaslab_try_hard_before_gang                              0
        zfs_mg_fragmentation_threshold                                95
        zfs_mg_noalloc_threshold                                       0
        zfs_min_metaslabs_to_flush                                     1
        zfs_multihost_fail_intervals                                  10
        zfs_multihost_history                                          0
        zfs_multihost_import_intervals                                20
        zfs_multihost_interval                                      1000
        zfs_multilist_num_sublists                                     0
        zfs_no_scrub_io                                                0
        zfs_no_scrub_prefetch                                          0
        zfs_nocacheflush                                               0
        zfs_nopwrite_enabled                                           1
        zfs_object_mutex_size                                         64
        zfs_obsolete_min_time_ms                                     500
        zfs_override_estimate_recordsize                               0
        zfs_pd_bytes_max                                        52428800
        zfs_per_txg_dirty_frees_percent                               30
        zfs_prefetch_disable                                           0
        zfs_read_history                                               0
        zfs_read_history_hits                                          0
        zfs_rebuild_max_segment                                  1048576
        zfs_rebuild_scrub_enabled                                      1
        zfs_rebuild_vdev_limit                                  67108864
        zfs_reconstruct_indirect_combinations_max                   4096
        zfs_recover                                                    0
        zfs_recv_queue_ff                                             20
        zfs_recv_queue_length                                   16777216
        zfs_recv_write_batch_size                                1048576
        zfs_removal_ignore_errors                                      0
        zfs_removal_suspend_progress                                   0
        zfs_remove_max_segment                                  16777216
        zfs_resilver_disable_defer                                     0
        zfs_resilver_min_time_ms                                    3000
        zfs_scan_blkstats                                              0
        zfs_scan_checkpoint_intval                                  7200
        zfs_scan_fill_weight                                           3
        zfs_scan_ignore_errors                                         0
        zfs_scan_issue_strategy                                        0
        zfs_scan_legacy                                                0
        zfs_scan_max_ext_gap                                     2097152
        zfs_scan_mem_lim_fact                                         20
        zfs_scan_mem_lim_soft_fact                                    20
        zfs_scan_strict_mem_lim                                        0
        zfs_scan_suspend_progress                                      0
        zfs_scan_vdev_limit                                     16777216
        zfs_scrub_min_time_ms                                       1000
        zfs_send_corrupt_data                                          0
        zfs_send_no_prefetch_queue_ff                                 20
        zfs_send_no_prefetch_queue_length                        1048576
        zfs_send_queue_ff                                             20
        zfs_send_queue_length                                   16777216
        zfs_send_unmodified_spill_blocks                               1
        zfs_slow_io_events_per_second                                 20
        zfs_spa_discard_memory_limit                            16777216
        zfs_special_class_metadata_reserve_pct                        25
        zfs_sync_pass_deferred_free                                    2
        zfs_sync_pass_dont_compress                                    8
        zfs_sync_pass_rewrite                                          2
        zfs_sync_taskq_batch_pct                                      75
        zfs_traverse_indirect_prefetch_limit                          32
        zfs_trim_extent_bytes_max                              134217728
        zfs_trim_extent_bytes_min                                  32768
        zfs_trim_metaslab_skip                                         0
        zfs_trim_queue_limit                                          10
        zfs_trim_txg_batch                                            32
        zfs_txg_history                                              100
        zfs_txg_timeout                                                5
        zfs_unflushed_log_block_max                               131072
        zfs_unflushed_log_block_min                                 1000
        zfs_unflushed_log_block_pct                                  400
        zfs_unflushed_log_txg_max                                   1000
        zfs_unflushed_max_mem_amt                             1073741824
        zfs_unflushed_max_mem_ppm                                   1000
        zfs_unlink_suspend_progress                                    0
        zfs_user_indirect_is_special                                   1
        zfs_vdev_aggregate_trim                                        0
        zfs_vdev_aggregation_limit                               1048576
        zfs_vdev_aggregation_limit_non_rotating                   131072
        zfs_vdev_async_read_max_active                                 3
        zfs_vdev_async_read_min_active                                 1
        zfs_vdev_async_write_active_max_dirty_percent                 60
        zfs_vdev_async_write_active_min_dirty_percent                 30
        zfs_vdev_async_write_max_active                               10
        zfs_vdev_async_write_min_active                                2
        zfs_vdev_cache_bshift                                         16
        zfs_vdev_cache_max                                         16384
        zfs_vdev_cache_size                                            0
        zfs_vdev_default_ms_count                                    200
        zfs_vdev_default_ms_shift                                     29
        zfs_vdev_initializing_max_active                               1
        zfs_vdev_initializing_min_active                               1
        zfs_vdev_max_active                                         1000
        zfs_vdev_max_auto_ashift                                      14
        zfs_vdev_min_auto_ashift                                       9
        zfs_vdev_min_ms_count                                         16
        zfs_vdev_mirror_non_rotating_inc                               0
        zfs_vdev_mirror_non_rotating_seek_inc                          1
        zfs_vdev_mirror_rotating_inc                                   0
        zfs_vdev_mirror_rotating_seek_inc                              5
        zfs_vdev_mirror_rotating_seek_offset                     1048576
        zfs_vdev_ms_count_limit                                   131072
        zfs_vdev_nia_credit                                            5
        zfs_vdev_nia_delay                                             5
        zfs_vdev_open_timeout_ms                                    1000
        zfs_vdev_queue_depth_pct                                    1000
        zfs_vdev_raidz_impl cycle [fastest] original scalar sse2 ssse3 avx2
        zfs_vdev_read_gap_limit                                    32768
        zfs_vdev_rebuild_max_active                                    3
        zfs_vdev_rebuild_min_active                                    1
        zfs_vdev_removal_max_active                                    2
        zfs_vdev_removal_min_active                                    1
        zfs_vdev_scheduler                                        unused
        zfs_vdev_scrub_max_active                                      3
        zfs_vdev_scrub_min_active                                      1
        zfs_vdev_sync_read_max_active                                 10
        zfs_vdev_sync_read_min_active                                 10
        zfs_vdev_sync_write_max_active                                10
        zfs_vdev_sync_write_min_active                                10
        zfs_vdev_trim_max_active                                       2
        zfs_vdev_trim_min_active                                       1
        zfs_vdev_write_gap_limit                                    4096
        zfs_vnops_read_chunk_size                                1048576
        zfs_wrlog_data_max                                    1634301542
        zfs_zevent_len_max                                           512
        zfs_zevent_retain_expire_secs                                900
        zfs_zevent_retain_max                                       2000
        zfs_zil_clean_taskq_maxalloc                             1048576
        zfs_zil_clean_taskq_minalloc                                1024
        zfs_zil_clean_taskq_nthr_pct                                 100
        zil_maxblocksize                                          131072
        zil_nocacheflush                                               0
        zil_replay_disable                                             0
        zil_slog_bulk                                             786432
        zio_deadman_log_all                                            0
        zio_dva_throttle_enabled                                       1
        zio_requeue_io_start_cut_in_line                               1
        zio_slow_io_ms                                             30000
        zio_taskq_batch_pct                                           80
        zio_taskq_batch_tpq                                            0
        zvol_inhibit_dev                                               0
        zvol_major                                                   230
        zvol_max_discard_blocks                                    16384
        zvol_prefetch_bytes                                       131072
        zvol_request_sync                                              0
        zvol_threads                                                  32
        zvol_volmode                                                   1

VDEV cache disabled, skipping section

ZIL committed transactions:                                         8.7k
        Commit requests:                                             493
        Flushes to stable storage:                                   491
        Transactions to SLOG storage pool:            0 Bytes          0
        Transactions to non-SLOG storage pool:       39.8 MiB        687

```

---

### Post by MAFoElffen on 2023-04-18
With what I said about doing real-world benchmark test:
```

sudo apt update
sudo apt install fio
# navigate to where you want the benchmark to test. Make sure you have at least 2GB free space.
fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
This is on a 5400 rpm 8TB SATA drive (my datapool drive):
```

mafoelffen@Mikes-B460M:/data/ISO$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [m(1)][11.7%][r=8KiB/s,w=8KiB/s][r=2,w=2 IOPS][eta 00m:53s] 
Jobs: 1 (f=1): [m(1)][20.0%][r=12KiB/s,w=16KiB/s][r=3,w=4 IOPS][eta 00m:48s]
Jobs: 1 (f=1): [m(1)][28.3%][r=4KiB/s,w=12KiB/s][r=1,w=3 IOPS][eta 00m:43s]  
Jobs: 1 (f=1): [m(1)][36.7%][r=108KiB/s,w=124KiB/s][r=27,w=31 IOPS][eta 00m:38s] 
Jobs: 1 (f=1): [m(1)][45.0%][r=144KiB/s,w=144KiB/s][r=36,w=36 IOPS][eta 00m:33s]
Jobs: 1 (f=1): [m(1)][53.3%][r=296KiB/s,w=240KiB/s][r=74,w=60 IOPS][eta 00m:28s]
Jobs: 1 (f=1): [m(1)][61.7%][r=252KiB/s,w=252KiB/s][r=63,w=63 IOPS][eta 00m:23s]
Jobs: 1 (f=1): [m(1)][70.0%][r=324KiB/s,w=256KiB/s][r=81,w=64 IOPS][eta 00m:18s]
Jobs: 1 (f=1): [m(1)][78.3%][r=244KiB/s,w=256KiB/s][r=61,w=64 IOPS][eta 00m:13s]
Jobs: 1 (f=1): [m(1)][86.7%][r=348KiB/s,w=256KiB/s][r=87,w=64 IOPS][eta 00m:08s] 
Jobs: 1 (f=1): [m(1)][95.0%][r=232KiB/s,w=260KiB/s][r=58,w=65 IOPS][eta 00m:03s] 
Jobs: 1 (f=0): [f(1)][100.0%][r=208KiB/s,w=248KiB/s][r=52,w=62 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3326565: Tue Apr 18 10:40:08 2023
  read: IOPS=33, BW=133KiB/s (136kB/s)(7968KiB/60011msec)
    slat (nsec): min=2155, max=74476, avg=14108.12, stdev=9816.53
    clat (nsec): min=186, max=15357, avg=571.82, stdev=1052.11
     lat (nsec): min=2417, max=75829, avg=14823.60, stdev=10083.27
    clat percentiles (nsec):
     |  1.00th=[  199],  5.00th=[  209], 10.00th=[  219], 20.00th=[  255],
     | 30.00th=[  306], 40.00th=[  334], 50.00th=[  486], 60.00th=[  620],
     | 70.00th=[  668], 80.00th=[  732], 90.00th=[  764], 95.00th=[  804],
     | 99.00th=[ 1208], 99.50th=[14400], 99.90th=[15296], 99.95th=[15296],
     | 99.99th=[15296]
   bw (  KiB/s): min=    8, max=  400, per=100.00%, avg=157.84, stdev=112.39, samples=100
   iops        : min=    2, max=  100, avg=39.46, stdev=28.10, samples=100
  write: IOPS=35, BW=140KiB/s (144kB/s)(8420KiB/60011msec); 0 zone resets
    slat (nsec): min=5545, max=73177, avg=20301.90, stdev=10317.62
    clat (nsec): min=242, max=16414, avg=627.37, stdev=867.87
     lat (nsec): min=5902, max=74153, avg=21073.13, stdev=10481.38
    clat percentiles (nsec):
     |  1.00th=[  270],  5.00th=[  290], 10.00th=[  310], 20.00th=[  354],
     | 30.00th=[  386], 40.00th=[  426], 50.00th=[  556], 60.00th=[  732],
     | 70.00th=[  764], 80.00th=[  788], 90.00th=[  820], 95.00th=[  860],
     | 99.00th=[ 1240], 99.50th=[ 1640], 99.90th=[15040], 99.95th=[15296],
     | 99.99th=[16512]
   bw (  KiB/s): min=    8, max=  264, per=100.00%, avg=144.35, stdev=112.76, samples=115
   iops        : min=    2, max=   66, avg=36.09, stdev=28.19, samples=115
  lat (nsec)   : 250=9.57%, 500=39.54%, 750=26.34%, 1000=22.58%
  lat (usec)   : 2=1.51%, 4=0.02%, 10=0.02%, 20=0.41%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=14, max=18214, avg=143.07, stdev=825.17
    sync percentiles (nsec):
     |  1.00th=[   15],  5.00th=[   16], 10.00th=[   18], 20.00th=[   22],
     | 30.00th=[   27], 40.00th=[   33], 50.00th=[  105], 60.00th=[  141],
     | 70.00th=[  143], 80.00th=[  145], 90.00th=[  153], 95.00th=[  173],
     | 99.00th=[  900], 99.50th=[  980], 99.90th=[16768], 99.95th=[17024],
     | 99.99th=[18304]
  cpu          : usr=0.05%, sys=0.20%, ctx=4216, majf=14, minf=15
  IO depths    : 1=199.9%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1992,2105,0,4094 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=133KiB/s (136kB/s), 133KiB/s-133KiB/s (136kB/s-136kB/s), io=7968KiB (8159kB), run=60011-60011msec
  WRITE: bw=140KiB/s (144kB/s), 140KiB/s-140KiB/s (144kB/s-144kB/s), io=8420KiB (8622kB), run=60011-60011msec
mafoelffen@Mikes-B460M:/data/ISO$ rm temp.file

```
And on my NVMe rpool drive:
```

mafoelffen@Mikes-B460M:~/Scripts$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [m(1)][11.7%][r=14.2MiB/s,w=14.4MiB/s][r=3642,w=3676 IOPS][eta 00m:53s]
Jobs: 1 (f=1): [m(1)][21.7%][r=12.1MiB/s,w=11.6MiB/s][r=3100,w=2976 IOPS][eta 00m:47s] 
Jobs: 1 (f=1): [m(1)][31.7%][r=14.6MiB/s,w=14.5MiB/s][r=3729,w=3721 IOPS][eta 00m:41s] 
Jobs: 1 (f=1): [m(1)][40.0%][r=11.2MiB/s,w=11.7MiB/s][r=2859,w=2991 IOPS][eta 00m:36s] 
Jobs: 1 (f=1): [m(1)][50.0%][r=10.9MiB/s,w=10.8MiB/s][r=2802,w=2774 IOPS][eta 00m:30s] 
Jobs: 1 (f=1): [m(1)][58.3%][r=9024KiB/s,w=9112KiB/s][r=2256,w=2278 IOPS][eta 00m:25s] 
Jobs: 1 (f=1): [m(1)][68.3%][r=13.4MiB/s,w=13.3MiB/s][r=3440,w=3407 IOPS][eta 00m:19s] 
Jobs: 1 (f=1): [m(1)][78.3%][r=12.0MiB/s,w=12.0MiB/s][r=3073,w=3062 IOPS][eta 00m:13s] 
Jobs: 1 (f=1): [m(1)][88.3%][r=11.9MiB/s,w=11.9MiB/s][r=3054,w=3034 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [m(1)][96.7%][r=14.7MiB/s,w=14.3MiB/s][r=3751,w=3652 IOPS][eta 00m:02s] 
Jobs: 1 (f=0): [f(1)][100.0%][r=12.9MiB/s,w=12.5MiB/s][r=3295,w=3198 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3332883: Tue Apr 18 10:42:53 2023
  read: IOPS=3000, BW=11.7MiB/s (12.3MB/s)(703MiB/60001msec)
    slat (nsec): min=1500, max=329595, avg=8615.77, stdev=7905.76
    clat (nsec): min=181, max=28677, avg=356.76, stdev=295.94
     lat (nsec): min=1781, max=332259, avg=9080.35, stdev=8021.92
    clat percentiles (nsec):
     |  1.00th=[  203],  5.00th=[  213], 10.00th=[  221], 20.00th=[  237],
     | 30.00th=[  266], 40.00th=[  326], 50.00th=[  354], 60.00th=[  374],
     | 70.00th=[  402], 80.00th=[  442], 90.00th=[  486], 95.00th=[  524],
     | 99.00th=[  636], 99.50th=[  748], 99.90th=[ 1848], 99.95th=[ 2576],
     | 99.99th=[18304]
   bw (  KiB/s): min= 1224, max=16120, per=99.93%, avg=11995.36, stdev=3539.96, samples=119
   iops        : min=  306, max= 4030, avg=2998.84, stdev=884.99, samples=119
  write: IOPS=2994, BW=11.7MiB/s (12.3MB/s)(702MiB/60001msec); 0 zone resets
    slat (usec): min=3, max=442, avg=12.09, stdev= 8.86
    clat (nsec): min=231, max=30649, avg=421.32, stdev=327.93
     lat (usec): min=4, max=448, avg=12.64, stdev= 8.98
    clat percentiles (nsec):
     |  1.00th=[  266],  5.00th=[  282], 10.00th=[  294], 20.00th=[  318],
     | 30.00th=[  350], 40.00th=[  394], 50.00th=[  414], 60.00th=[  430],
     | 70.00th=[  454], 80.00th=[  494], 90.00th=[  540], 95.00th=[  572],
     | 99.00th=[  700], 99.50th=[  804], 99.90th=[ 2128], 99.95th=[ 2864],
     | 99.99th=[18560]
   bw (  KiB/s): min= 1224, max=15120, per=99.96%, avg=11972.44, stdev=3538.38, samples=119
   iops        : min=  306, max= 3780, avg=2993.11, stdev=884.60, samples=119
  lat (nsec)   : 250=13.12%, 500=73.54%, 750=12.73%, 1000=0.36%
  lat (usec)   : 2=0.14%, 4=0.07%, 10=0.01%, 20=0.02%, 50=0.01%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=10, max=19053, avg=67.39, stdev=124.66
    sync percentiles (nsec):
     |  1.00th=[   15],  5.00th=[   16], 10.00th=[   18], 20.00th=[   24],
     | 30.00th=[   25], 40.00th=[   27], 50.00th=[   61], 60.00th=[   92],
     | 70.00th=[  104], 80.00th=[  112], 90.00th=[  120], 95.00th=[  126],
     | 99.00th=[  149], 99.50th=[  173], 99.90th=[  692], 99.95th=[  876],
     | 99.99th=[ 1768]
  cpu          : usr=1.08%, sys=9.84%, ctx=359731, majf=0, minf=15
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=180053,179646,0,359696 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=11.7MiB/s (12.3MB/s), 11.7MiB/s-11.7MiB/s (12.3MB/s-12.3MB/s), io=703MiB (737MB), run=60001-60001msec
  WRITE: bw=11.7MiB/s (12.3MB/s), 11.7MiB/s-11.7MiB/s (12.3MB/s-12.3MB/s), io=702MiB (736MB), run=60001-60001msec
mafoelffen@Mikes-B460M:~/Scripts$ rm temp.file

```
That is going to show worst-case, real-world, random read/write speed.

---

### Post by papriak on 2023-04-18
> **MAFoElffen said:**
> With what I said about doing real-world benchmark test:
```

sudo apt update
sudo apt install fio
# navigate to where you want the benchmark to test. Make sure you have at least 2GB free space.
fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
This is on a 5400 rpm 8TB SATA drive (my datapool drive):
```

mafoelffen@Mikes-B460M:/data/ISO$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [m(1)][11.7%][r=8KiB/s,w=8KiB/s][r=2,w=2 IOPS][eta 00m:53s] 
Jobs: 1 (f=1): [m(1)][20.0%][r=12KiB/s,w=16KiB/s][r=3,w=4 IOPS][eta 00m:48s]
Jobs: 1 (f=1): [m(1)][28.3%][r=4KiB/s,w=12KiB/s][r=1,w=3 IOPS][eta 00m:43s]  
Jobs: 1 (f=1): [m(1)][36.7%][r=108KiB/s,w=124KiB/s][r=27,w=31 IOPS][eta 00m:38s] 
Jobs: 1 (f=1): [m(1)][45.0%][r=144KiB/s,w=144KiB/s][r=36,w=36 IOPS][eta 00m:33s]
Jobs: 1 (f=1): [m(1)][53.3%][r=296KiB/s,w=240KiB/s][r=74,w=60 IOPS][eta 00m:28s]
Jobs: 1 (f=1): [m(1)][61.7%][r=252KiB/s,w=252KiB/s][r=63,w=63 IOPS][eta 00m:23s]
Jobs: 1 (f=1): [m(1)][70.0%][r=324KiB/s,w=256KiB/s][r=81,w=64 IOPS][eta 00m:18s]
Jobs: 1 (f=1): [m(1)][78.3%][r=244KiB/s,w=256KiB/s][r=61,w=64 IOPS][eta 00m:13s]
Jobs: 1 (f=1): [m(1)][86.7%][r=348KiB/s,w=256KiB/s][r=87,w=64 IOPS][eta 00m:08s] 
Jobs: 1 (f=1): [m(1)][95.0%][r=232KiB/s,w=260KiB/s][r=58,w=65 IOPS][eta 00m:03s] 
Jobs: 1 (f=0): [f(1)][100.0%][r=208KiB/s,w=248KiB/s][r=52,w=62 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3326565: Tue Apr 18 10:40:08 2023
  read: IOPS=33, BW=133KiB/s (136kB/s)(7968KiB/60011msec)
    slat (nsec): min=2155, max=74476, avg=14108.12, stdev=9816.53
    clat (nsec): min=186, max=15357, avg=571.82, stdev=1052.11
     lat (nsec): min=2417, max=75829, avg=14823.60, stdev=10083.27
    clat percentiles (nsec):
     |  1.00th=[  199],  5.00th=[  209], 10.00th=[  219], 20.00th=[  255],
     | 30.00th=[  306], 40.00th=[  334], 50.00th=[  486], 60.00th=[  620],
     | 70.00th=[  668], 80.00th=[  732], 90.00th=[  764], 95.00th=[  804],
     | 99.00th=[ 1208], 99.50th=[14400], 99.90th=[15296], 99.95th=[15296],
     | 99.99th=[15296]
   bw (  KiB/s): min=    8, max=  400, per=100.00%, avg=157.84, stdev=112.39, samples=100
   iops        : min=    2, max=  100, avg=39.46, stdev=28.10, samples=100
  write: IOPS=35, BW=140KiB/s (144kB/s)(8420KiB/60011msec); 0 zone resets
    slat (nsec): min=5545, max=73177, avg=20301.90, stdev=10317.62
    clat (nsec): min=242, max=16414, avg=627.37, stdev=867.87
     lat (nsec): min=5902, max=74153, avg=21073.13, stdev=10481.38
    clat percentiles (nsec):
     |  1.00th=[  270],  5.00th=[  290], 10.00th=[  310], 20.00th=[  354],
     | 30.00th=[  386], 40.00th=[  426], 50.00th=[  556], 60.00th=[  732],
     | 70.00th=[  764], 80.00th=[  788], 90.00th=[  820], 95.00th=[  860],
     | 99.00th=[ 1240], 99.50th=[ 1640], 99.90th=[15040], 99.95th=[15296],
     | 99.99th=[16512]
   bw (  KiB/s): min=    8, max=  264, per=100.00%, avg=144.35, stdev=112.76, samples=115
   iops        : min=    2, max=   66, avg=36.09, stdev=28.19, samples=115
  lat (nsec)   : 250=9.57%, 500=39.54%, 750=26.34%, 1000=22.58%
  lat (usec)   : 2=1.51%, 4=0.02%, 10=0.02%, 20=0.41%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=14, max=18214, avg=143.07, stdev=825.17
    sync percentiles (nsec):
     |  1.00th=[   15],  5.00th=[   16], 10.00th=[   18], 20.00th=[   22],
     | 30.00th=[   27], 40.00th=[   33], 50.00th=[  105], 60.00th=[  141],
     | 70.00th=[  143], 80.00th=[  145], 90.00th=[  153], 95.00th=[  173],
     | 99.00th=[  900], 99.50th=[  980], 99.90th=[16768], 99.95th=[17024],
     | 99.99th=[18304]
  cpu          : usr=0.05%, sys=0.20%, ctx=4216, majf=14, minf=15
  IO depths    : 1=199.9%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=1992,2105,0,4094 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=133KiB/s (136kB/s), 133KiB/s-133KiB/s (136kB/s-136kB/s), io=7968KiB (8159kB), run=60011-60011msec
  WRITE: bw=140KiB/s (144kB/s), 140KiB/s-140KiB/s (144kB/s-144kB/s), io=8420KiB (8622kB), run=60011-60011msec
mafoelffen@Mikes-B460M:/data/ISO$ rm temp.file

```
And on my NVMe rpool drive:
```

mafoelffen@Mikes-B460M:~/Scripts$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [m(1)][11.7%][r=14.2MiB/s,w=14.4MiB/s][r=3642,w=3676 IOPS][eta 00m:53s]
Jobs: 1 (f=1): [m(1)][21.7%][r=12.1MiB/s,w=11.6MiB/s][r=3100,w=2976 IOPS][eta 00m:47s] 
Jobs: 1 (f=1): [m(1)][31.7%][r=14.6MiB/s,w=14.5MiB/s][r=3729,w=3721 IOPS][eta 00m:41s] 
Jobs: 1 (f=1): [m(1)][40.0%][r=11.2MiB/s,w=11.7MiB/s][r=2859,w=2991 IOPS][eta 00m:36s] 
Jobs: 1 (f=1): [m(1)][50.0%][r=10.9MiB/s,w=10.8MiB/s][r=2802,w=2774 IOPS][eta 00m:30s] 
Jobs: 1 (f=1): [m(1)][58.3%][r=9024KiB/s,w=9112KiB/s][r=2256,w=2278 IOPS][eta 00m:25s] 
Jobs: 1 (f=1): [m(1)][68.3%][r=13.4MiB/s,w=13.3MiB/s][r=3440,w=3407 IOPS][eta 00m:19s] 
Jobs: 1 (f=1): [m(1)][78.3%][r=12.0MiB/s,w=12.0MiB/s][r=3073,w=3062 IOPS][eta 00m:13s] 
Jobs: 1 (f=1): [m(1)][88.3%][r=11.9MiB/s,w=11.9MiB/s][r=3054,w=3034 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [m(1)][96.7%][r=14.7MiB/s,w=14.3MiB/s][r=3751,w=3652 IOPS][eta 00m:02s] 
Jobs: 1 (f=0): [f(1)][100.0%][r=12.9MiB/s,w=12.5MiB/s][r=3295,w=3198 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3332883: Tue Apr 18 10:42:53 2023
  read: IOPS=3000, BW=11.7MiB/s (12.3MB/s)(703MiB/60001msec)
    slat (nsec): min=1500, max=329595, avg=8615.77, stdev=7905.76
    clat (nsec): min=181, max=28677, avg=356.76, stdev=295.94
     lat (nsec): min=1781, max=332259, avg=9080.35, stdev=8021.92
    clat percentiles (nsec):
     |  1.00th=[  203],  5.00th=[  213], 10.00th=[  221], 20.00th=[  237],
     | 30.00th=[  266], 40.00th=[  326], 50.00th=[  354], 60.00th=[  374],
     | 70.00th=[  402], 80.00th=[  442], 90.00th=[  486], 95.00th=[  524],
     | 99.00th=[  636], 99.50th=[  748], 99.90th=[ 1848], 99.95th=[ 2576],
     | 99.99th=[18304]
   bw (  KiB/s): min= 1224, max=16120, per=99.93%, avg=11995.36, stdev=3539.96, samples=119
   iops        : min=  306, max= 4030, avg=2998.84, stdev=884.99, samples=119
  write: IOPS=2994, BW=11.7MiB/s (12.3MB/s)(702MiB/60001msec); 0 zone resets
    slat (usec): min=3, max=442, avg=12.09, stdev= 8.86
    clat (nsec): min=231, max=30649, avg=421.32, stdev=327.93
     lat (usec): min=4, max=448, avg=12.64, stdev= 8.98
    clat percentiles (nsec):
     |  1.00th=[  266],  5.00th=[  282], 10.00th=[  294], 20.00th=[  318],
     | 30.00th=[  350], 40.00th=[  394], 50.00th=[  414], 60.00th=[  430],
     | 70.00th=[  454], 80.00th=[  494], 90.00th=[  540], 95.00th=[  572],
     | 99.00th=[  700], 99.50th=[  804], 99.90th=[ 2128], 99.95th=[ 2864],
     | 99.99th=[18560]
   bw (  KiB/s): min= 1224, max=15120, per=99.96%, avg=11972.44, stdev=3538.38, samples=119
   iops        : min=  306, max= 3780, avg=2993.11, stdev=884.60, samples=119
  lat (nsec)   : 250=13.12%, 500=73.54%, 750=12.73%, 1000=0.36%
  lat (usec)   : 2=0.14%, 4=0.07%, 10=0.01%, 20=0.02%, 50=0.01%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=10, max=19053, avg=67.39, stdev=124.66
    sync percentiles (nsec):
     |  1.00th=[   15],  5.00th=[   16], 10.00th=[   18], 20.00th=[   24],
     | 30.00th=[   25], 40.00th=[   27], 50.00th=[   61], 60.00th=[   92],
     | 70.00th=[  104], 80.00th=[  112], 90.00th=[  120], 95.00th=[  126],
     | 99.00th=[  149], 99.50th=[  173], 99.90th=[  692], 99.95th=[  876],
     | 99.99th=[ 1768]
  cpu          : usr=1.08%, sys=9.84%, ctx=359731, majf=0, minf=15
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=180053,179646,0,359696 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=11.7MiB/s (12.3MB/s), 11.7MiB/s-11.7MiB/s (12.3MB/s-12.3MB/s), io=703MiB (737MB), run=60001-60001msec
  WRITE: bw=11.7MiB/s (12.3MB/s), 11.7MiB/s-11.7MiB/s (12.3MB/s-12.3MB/s), io=702MiB (736MB), run=60001-60001msec
mafoelffen@Mikes-B460M:~/Scripts$ rm temp.file

```
That is going to show worst-case, real-world, random read/write speed.

Here's are my pool's results:

```
TEST: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=813684: Tue Apr 18 11:26:57 2023
  read: IOPS=87, BW=351KiB/s (360kB/s)(20.6MiB/60007msec)
    slat (usec): min=12, max=669, avg=60.71, stdev=42.71
    clat (nsec): min=575, max=10568, avg=1497.47, stdev=567.89
     lat (usec): min=13, max=677, avg=62.46, stdev=43.12
    clat percentiles (nsec):
     |  1.00th=[  668],  5.00th=[  924], 10.00th=[  988], 20.00th=[ 1032],
     | 30.00th=[ 1096], 40.00th=[ 1224], 50.00th=[ 1432], 60.00th=[ 1768],
     | 70.00th=[ 1800], 80.00th=[ 1832], 90.00th=[ 1944], 95.00th=[ 1992],
     | 99.00th=[ 3024], 99.50th=[ 4960], 99.90th=[ 6816], 99.95th=[ 9408],
     | 99.99th=[10560]
   bw (  KiB/s): min=   16, max=  688, per=99.88%, avg=351.53, stdev=136.40, samples=119
   iops        : min=    4, max=  172, avg=87.88, stdev=34.10, samples=119
  write: IOPS=88, BW=355KiB/s (363kB/s)(20.8MiB/60007msec); 0 zone resets
    slat (usec): min=44, max=804, avg=102.25, stdev=45.43
    clat (nsec): min=688, max=17424, avg=1627.60, stdev=589.89
     lat (usec): min=45, max=812, avg=104.17, stdev=45.83
    clat percentiles (nsec):
     |  1.00th=[  796],  5.00th=[ 1128], 10.00th=[ 1176], 20.00th=[ 1224],
     | 30.00th=[ 1272], 40.00th=[ 1432], 50.00th=[ 1608], 60.00th=[ 1832],
     | 70.00th=[ 1864], 80.00th=[ 1912], 90.00th=[ 1992], 95.00th=[ 2064],
     | 99.00th=[ 3536], 99.50th=[ 5280], 99.90th=[ 6880], 99.95th=[10304],
     | 99.99th=[17536]
   bw (  KiB/s): min=   64, max=  480, per=99.77%, avg=354.76, stdev=111.20, samples=119
   iops        : min=   16, max=  120, avg=88.69, stdev=27.80, samples=119
  lat (nsec)   : 750=1.19%, 1000=6.73%
  lat (usec)   : 2=85.29%, 4=6.14%, 10=0.61%, 20=0.04%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=34, max=14292, avg=251.48, stdev=729.90
    sync percentiles (nsec):
     |  1.00th=[   47],  5.00th=[   63], 10.00th=[   66], 20.00th=[   75],
     | 30.00th=[   86], 40.00th=[   97], 50.00th=[  201], 60.00th=[  302],
     | 70.00th=[  302], 80.00th=[  306], 90.00th=[  306], 95.00th=[  310],
     | 99.00th=[  868], 99.50th=[ 1080], 99.90th=[10816], 99.95th=[11328],
     | 99.99th=[11968]
  cpu          : usr=0.18%, sys=2.12%, ctx=10877, majf=0, minf=16
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=5272,5323,0,10592 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=351KiB/s (360kB/s), 351KiB/s-351KiB/s (360kB/s-360kB/s), io=20.6MiB (21.6MB), run=60007-60007msec
  WRITE: bw=355KiB/s (363kB/s), 355KiB/s-355KiB/s (363kB/s-363kB/s), io=20.8MiB (21.8MB), run=60007-60007msec

```


Edit:  Shouldn't I be getting some sort of RAID0-like speed boost, minus the processing overhead?  That would explain how I was getting a few hundred MB/s transfer speeds before.

---

### Post by TheFu on 2023-04-18
I know little about ZFS, but I'd check each device separately for performance issues. 1 slow drive can make the entire array slower.

It is also possible to tune different parts of each disk for performance of the specific workload.  Lots of tiny files or running a DBMS is different from accessing 1G+ files.  hdparm is how I've done it ... and have some settings reloaded with every boot to ensure the same performance.

I'd also start to see of the SMART data for each device is showing cable issues via ECC error corrections or retries.

Check everything for the simplest storage setup, then move out, adding complexity.  The last things to add once you have all the performance verified locally just on the system would be networking and finally samba.  Misconfiguration at any level can harm performance.

It will take some time and you may find that some things, like drive controllers/HBAs are the root issue that can't be easily fixed today.  That happened to me.  The only way I got better performance was to stop using the methodboard disk controller and switch to an LSI HBA.

One last thing. Don't use USB connections for any RAID devices. Just. Don't.

---

### Post by #&amp;thj^% on 2023-04-18
EDIT: Ninja'd by tTheFu
From my rpool, just to see a diif:
```
**_on Tue Apr 18 at 12:43 PM in ~ branch: (HEAD) _**
Run status group 0 (all jobs):
   READ: bw=1142KiB/s (1170kB/s), 1142KiB/s-1142KiB/s (1170kB/s-1170kB/s), io=66.9MiB (70.2MB), run=60001-60001msec
  WRITE: bw=1143KiB/s (1170kB/s), 1143KiB/s-1143KiB/s (1170kB/s-1170kB/s), io=67.0MiB (70.2MB), run=60001-60001msec

```
From  /pool3:
```
**_on Tue Apr 18 at 12:54 PM in /pool3 branch: (HEAD) _**
##Skip to the bottom###
Run status group 0 (all jobs):
   READ: bw=1142KiB/s (1170kB/s), 1142KiB/s-1142KiB/s (1170kB/s-1170kB/s), io=66.9MiB (70.2MB), run=60001-60001msec
  WRITE: bw=1143KiB/s (1170kB/s), 1143KiB/s-1143KiB/s (1170kB/s-1170kB/s), io=67.0MiB (70.2MB), run=60001-60001msec

```
And on a spinning Drive (USB)
```
**_on Tue Apr 18 at 12:01 PM in /media/me/My Passport branch: (HEAD) _**
Run status group 0 (all jobs):
   READ: bw=329KiB/s (337kB/s), 329KiB/s-329KiB/s (337kB/s-337kB/s), io=19.3MiB (20.2MB), run=60007-60007msec
  WRITE: bw=333KiB/s (341kB/s), 333KiB/s-333KiB/s (341kB/s-341kB/s), io=19.5MiB (20.5MB), run=60007-60007msec

Disk stats (read/write):
  sdc: ios=4421/19899, merge=0/0, ticks=51260/5794, in_queue=57054, util=99.99%
```


I'm going to step aside for MAFoElffen on this thread.

---

### Post by MAFoElffen on 2023-04-18
> **TheFu said:**
> I know little about ZFS, but I'd check each device separately for performance issues. 1 slow drive can make the entire array slower.

It is also possible to tune different parts of each disk for performance of the specific workload.  Lots of tiny files or running a DBMS is different from accessing 1G+ files.  hdparm is how I've done it ... and have some settings reloaded with every boot to ensure the same performance.

I'd also start to see of the SMART data for each device is showing cable issues via ECC error corrections or retries.

Check everything for the simplest storage setup, then move out, adding complexity.  The last things to add once you have all the performance verified locally just on the system would be networking and finally samba.  Misconfiguration at any level can harm performance.

It will take some time and you may find that some things, like drive controllers/HBAs are the root issue that can't be easily fixed today.  That happened to me.  The only way I got better performance was to stop using the methodboard disk controller and switch to an LSI HBA.

One last thing. Don't use USB connections for any RAID devices. Just. Don't.
He should have probably linked ihs last thread, so you could have seen what he has and is using...

He has 8 identical (HGST Ultrastar 7K4000 HUS724040ALE640) 4TB drives that he bought "after" they were retired. The Controller is a Dell PERC H310, re-flashed to IT/mode, so the controller is seen as "LSI SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon]", with the drives pass-through. I know that controller is 6GB. The ARC is at Default right now, which for the system 32GB RAM is set for a high limit of 16GB.

I don't think what he is getting for benchmarks is off for using a Dell PERC H310. I personally think that is where the possible bottleneck is.

This is like his sytem, but showed that just by switching out the H310 with an IBM Serveraid M1015 SAS/SATA Controller HBA, the results were whole lots better. You can pick up one of those used for $15-$30.  RE: [https://www.truenas.com/community/threads/poor-performance-on-dell-r720-with-h310-mini-flashed-to-it-mode.91644/](https://www.truenas.com/community/threads/poor-performance-on-dell-r720-with-h310-mini-flashed-to-it-mode.91644/)

Yes. The H310 does not have a good track record--> The performance on PERC H310's: [GOOGLE Search on Poor Performance Dell PERC H310]("https://www.google.com/search?q=poor+performance+dell+perc+h310&client=ubuntu-sn&channel=fs&sxsrf=APwXEdcwRxYK0O7tk1FgbVnxS2SHs67ppQ%3A1681848143397&ei=T_c-ZPXsF63JkPIP9eOisAQ&ved=0ahUKEwi10JzJnLT-AhWtJEQIHfWxCEYQ4dUDCA8&uact=5&oq=poor+performance+dell+perc+h310&gs_lcp=Cgxnd3Mtd2l6LXNlcnAQAzIECCMQJzIECCMQJzoHCCMQsAMQJzoLCAAQigUQhgMQsANKBAhBGAFQ3ApY3zBg2zpoAXAAeACAAa4BiAHuFZIBBDAuMTmYAQCgAQHIAQTAAQE&sclient=gws-wiz-serp#ip=1")

Like I said, what I posted was probably going to show it's worst case scenario of a benchmark.

To see the best case w/ the same tool:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
The stats using those are probably going to be closer to the advertised stats of drives.

And to check each drive individually, for comparison:
```

sudo hdparm -t -T /dev/sd[a-g]

```
As a quick check, I just usually just use 
```

sudo zpool iostat -v

```

---

### Post by papriak on 2023-04-18
> **MAFoElffen said:**
> To see the best case w/ the same tool:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
The stats using those are probably going to be closer to the advertised stats of drives.

Read:
```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=3642134: Tue Apr 18 14:54:17 2023
  read: IOPS=2953, BW=2954MiB/s (3097MB/s)(10.0GiB/3467msec)
    slat (usec): min=15, max=198, avg=74.16, stdev=20.39
    clat (usec): min=563, max=21097, avg=10727.56, stdev=1091.16
     lat (usec): min=582, max=21115, avg=10802.18, stdev=1088.37
    clat percentiles (usec):
     |  1.00th=[ 5604],  5.00th=[10683], 10.00th=[10683], 20.00th=[10683],
     | 30.00th=[10683], 40.00th=[10683], 50.00th=[10683], 60.00th=[10683],
     | 70.00th=[10814], 80.00th=[10814], 90.00th=[10945], 95.00th=[11076],
     | 99.00th=[14091], 99.50th=[17433], 99.90th=[20317], 99.95th=[20841],
     | 99.99th=[20841]
   bw (  MiB/s): min= 2934, max= 2962, per=100.00%, avg=2955.00, stdev=11.01, samples=6
   iops        : min= 2934, max= 2962, avg=2955.00, stdev=11.01, samples=6
  lat (usec)   : 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.03%, 4=0.56%, 10=1.87%, 20=97.37%, 50=0.16%
  cpu          : usr=4.21%, sys=26.86%, ctx=10208, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2954MiB/s (3097MB/s), 2954MiB/s-2954MiB/s (3097MB/s-3097MB/s), io=10.0GiB (10.7GB), run=3467-3467msec

Disk stats (read/write):
  nvme0n1: ios=9767/16, merge=0/40, ticks=103667/4, in_queue=103672, util=97.47%

```

Write:
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=3642609: Tue Apr 18 14:56:10 2023
  write: IOPS=994, BW=994MiB/s (1043MB/s)(10.0GiB/10298msec); 0 zone resets
    slat (usec): min=17, max=30323, avg=152.28, stdev=398.03
    clat (usec): min=3315, max=65019, avg=31969.71, stdev=4821.92
     lat (usec): min=3532, max=65176, avg=32122.85, stdev=4812.38
    clat percentiles (usec):
     |  1.00th=[12125],  5.00th=[28705], 10.00th=[28705], 20.00th=[28705],
     | 30.00th=[28967], 40.00th=[30016], 50.00th=[33424], 60.00th=[33817],
     | 70.00th=[34866], 80.00th=[34866], 90.00th=[35390], 95.00th=[35390],
     | 99.00th=[49546], 99.50th=[55313], 99.90th=[61604], 99.95th=[62129],
     | 99.99th=[64226]
   bw (  KiB/s): min=1007616, max=1030144, per=100.00%, avg=1019085.20, stdev=4855.63, samples=20
   iops        : min=  984, max= 1006, avg=995.20, stdev= 4.74, samples=20
  lat (msec)   : 4=0.03%, 10=0.74%, 20=0.90%, 50=97.35%, 100=0.98%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=941, max=941, avg=941.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  940],  5.00th=[  940], 10.00th=[  940], 20.00th=[  940],
     | 30.00th=[  940], 40.00th=[  940], 50.00th=[  940], 60.00th=[  940],
     | 70.00th=[  940], 80.00th=[  940], 90.00th=[  940], 95.00th=[  940],
     | 99.00th=[  940], 99.50th=[  940], 99.90th=[  940], 99.95th=[  940],
     | 99.99th=[  940]
  cpu          : usr=9.36%, sys=8.00%, ctx=10164, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=994MiB/s (1043MB/s), 994MiB/s-994MiB/s (1043MB/s-1043MB/s), io=10.0GiB (10.7GB), run=10298-10298msec

Disk stats (read/write):
  nvme0n1: ios=0/10081, merge=0/6, ticks=0/317978, in_queue=317999, util=99.06%

```

> 
And to check each drive individually, for comparison:
```

sudo hdparm -t -T /dev/sd[a-g]

```

```

/dev/sda:
 Timing cached reads:   28132 MB in  1.99 seconds = 14149.34 MB/sec
 Timing buffered disk reads: 492 MB in  3.00 seconds = 163.94 MB/sec

/dev/sdb:
 Timing cached reads:   28164 MB in  1.99 seconds = 14165.48 MB/sec
 Timing buffered disk reads: 516 MB in  3.01 seconds = 171.50 MB/sec

/dev/sdc:
 Timing cached reads:   28258 MB in  1.99 seconds = 14212.40 MB/sec
 Timing buffered disk reads: 520 MB in  3.01 seconds = 172.70 MB/sec

/dev/sdd:
 Timing cached reads:   29122 MB in  1.99 seconds = 14649.79 MB/sec
 Timing buffered disk reads: 518 MB in  3.00 seconds = 172.57 MB/sec

/dev/sde:
 Timing cached reads:   28562 MB in  1.99 seconds = 14366.11 MB/sec
 Timing buffered disk reads: 518 MB in  3.00 seconds = 172.40 MB/sec

/dev/sdf:
 Timing cached reads:   28262 MB in  1.99 seconds = 14214.77 MB/sec
 Timing buffered disk reads: 510 MB in  3.01 seconds = 169.53 MB/sec

/dev/sdg:
 Timing cached reads:   28910 MB in  1.99 seconds = 14542.30 MB/sec
 Timing buffered disk reads: 516 MB in  3.01 seconds = 171.66 MB/sec

/dev/sdh:
 Timing cached reads:   28706 MB in  1.99 seconds = 14439.05 MB/sec
 Timing buffered disk reads: 518 MB in  3.00 seconds = 172.49 MB/sec

```


> As a quick check, I just usually just use 
```

sudo zpool iostat -v

```

```
                              capacity     operations     bandwidth 
pool                        alloc   free   read  write   read  write
--------------------------  -----  -----  -----  -----  -----  -----
Pool                         561G  28.6T  21.7K    354  19.8M  1.37M
  raidz3-0                   561G  28.6T  21.7K    354  19.8M  1.37M
    wwn-0x5000cca249d1d3e2      -      -  2.71K     44  2.47M   176K
    wwn-0x5000cca249d2c49e      -      -  2.71K     44  2.47M   175K
    wwn-0x5000cca24ce9c080      -      -  2.72K     44  2.47M   175K
    wwn-0x5000cca249d18e47      -      -  2.71K     43  2.49M   175K
    wwn-0x5000cca24ceec499      -      -  2.71K     45  2.47M   176K
    wwn-0x5000cca24cee021f      -      -  2.71K     44  2.47M   175K
    wwn-0x5000cca24cf3fa7a      -      -  2.71K     44  2.47M   175K
    wwn-0x5000cca24cf51b3f      -      -  2.71K     43  2.49M   175K
--------------------------  -----  -----  -----  -----  -----  -----

```


Looks like the drives are faster than the pool to me.

---

### Post by MAFoElffen on 2023-04-18
Your /dev/nvme0n1 drive is faster than your SATA /dev/sdX hard drives, Yes... Notice the end of the tests where it says:
```

Disk stats (read/write):
  [COLOR=#ff0000]nvme0n1: [/COLOR]...

```
LOL. That tells me you were in a folder in your root drive that "wasn't" in your mounted RAIDZ3 pool when you ran those tests. Remember me saying to navigate to a folder within the pool to run it from? It happens.

Please rerun them from within your pool.

---

### Post by papriak on 2023-04-19
> **MAFoElffen said:**
> Your /dev/nvme0n1 drive is faster than your SATA /dev/sdX hard drives, Yes... Notice the end of the tests where it says:
```

Disk stats (read/write):
  [COLOR=#ff0000]nvme0n1: [/COLOR]...

```
LOL. That tells me you were in a folder in your root drive that "wasn't" in your mounted RAIDZ3 pool when you ran those tests. Remember me saying to navigate to a folder within the pool to run it from? It happens.

Please rerun them from within your pool.

Oops, sorry.

Fio test read:

```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=17824: Wed Apr 19 08:08:37 2023
  read: IOPS=103, BW=103MiB/s (108MB/s)(6197MiB/60004msec)
    slat (usec): min=4436, max=89507, avg=9676.27, stdev=6981.05
    clat (usec): min=3, max=795295, avg=296179.23, stdev=207697.29
     lat (msec): min=4, max=884, avg=305.86, stdev=214.40
    clat percentiles (msec):
     |  1.00th=[   73],  5.00th=[  153], 10.00th=[  153], 20.00th=[  155],
     | 30.00th=[  155], 40.00th=[  157], 50.00th=[  157], 60.00th=[  159],
     | 70.00th=[  567], 80.00th=[  575], 90.00th=[  609], 95.00th=[  617],
     | 99.00th=[  659], 99.50th=[  684], 99.90th=[  693], 99.95th=[  701],
     | 99.99th=[  793]
   bw (  KiB/s): min=14336, max=223232, per=99.60%, avg=105333.15, stdev=72468.35, samples=118
   iops        : min=   14, max=  218, avg=102.86, stdev=70.77, samples=118
  lat (usec)   : 4=0.06%
  lat (msec)   : 10=0.13%, 20=0.13%, 50=0.39%, 100=0.60%, 250=66.10%
  lat (msec)   : 500=0.27%, 750=32.29%, 1000=0.03%
  cpu          : usr=0.07%, sys=99.37%, ctx=655, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.3%, 8=0.5%, 16=1.0%, 32=98.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=6197,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=103MiB/s (108MB/s), 103MiB/s-103MiB/s (108MB/s-108MB/s), io=6197MiB (6498MB), run=60004-60004msec

```


Fio test write:

```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=520726: Wed Apr 19 08:09:49 2023
  write: IOPS=62, BW=62.1MiB/s (65.1MB/s)(3725MiB/60003msec); 0 zone resets
    slat (usec): min=8990, max=47821, avg=16096.76, stdev=3016.80
    clat (usec): min=9, max=640845, avg=495535.75, stdev=76095.37
     lat (msec): min=17, max=660, avg=511.63, stdev=77.92
    clat percentiles (msec):
     |  1.00th=[  279],  5.00th=[  338], 10.00th=[  393], 20.00th=[  468],
     | 30.00th=[  481], 40.00th=[  489], 50.00th=[  498], 60.00th=[  514],
     | 70.00th=[  531], 80.00th=[  542], 90.00th=[  584], 95.00th=[  592],
     | 99.00th=[  617], 99.50th=[  625], 99.90th=[  642], 99.95th=[  642],
     | 99.99th=[  642]
   bw (  KiB/s): min= 8192, max=100352, per=99.13%, avg=63018.57, stdev=10768.79, samples=119
   iops        : min=    8, max=   98, avg=61.51, stdev=10.53, samples=119
  lat (usec)   : 10=0.03%, 20=0.03%
  lat (msec)   : 20=0.05%, 50=0.08%, 100=0.13%, 250=0.48%, 500=50.39%
  lat (msec)   : 750=48.81%
  cpu          : usr=0.43%, sys=99.30%, ctx=3385, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.9%, 32=98.3%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3725,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=62.1MiB/s (65.1MB/s), 62.1MiB/s-62.1MiB/s (65.1MB/s-65.1MB/s), io=3725MiB (3906MB), run=60003-60003msec

```

---

### Post by MAFoElffen on 2023-04-19
As you have said and said is your mantra: "Life is too short to use slow computers"

RE: 
[https://www.ebay.com/itm/325614739010?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A19wIp10bmRa2IA0muPfHCTw18&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325614739010&targetid=1584571731043&device=c&mktype=&googleloc=9033423&poi=&campaignid=15275224983&mkgroupid=131097072938&rlsatarget=pla-1584571731043&abcId=9300697&merchantid=114727230&gclid=CjwKCAjwov6hBhBsEiwAvrvN6N9BFg86-hA8JduP20u2tJQnZEEuYpolgW4_Y_IqExjP2LnanstTQhoCvCkQAvD_BwE](https://www.ebay.com/itm/325614739010?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A19wIp10bmRa2IA0muPfHCTw18&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325614739010&targetid=1584571731043&device=c&mktype=&googleloc=9033423&poi=&campaignid=15275224983&mkgroupid=131097072938&rlsatarget=pla-1584571731043&abcId=9300697&merchantid=114727230&gclid=CjwKCAjwov6hBhBsEiwAvrvN6N9BFg86-hA8JduP20u2tJQnZEEuYpolgW4_Y_IqExjP2LnanstTQhoCvCkQAvD_BwE)

[https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675](https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675)

I think either of those would show quite a bit of difference with your baselines... Just to remove that bottleneck there. It's an investment that I think is worth it. This is one rare things that I think spending a little money will make a considerable worthwhile difference.

It would mean no changes in config (right now). Just pop the old card out and new card in. Retest the benchmarks and compare with your baseline.

The second would be to get a fast 512GB SSD to use as L2ARC cache. I have suggested this earlier... This is also something that I am adding to my own server (When I add more NVMe).
> 
When a system gets read requests, ZFS uses ARC (RAM) to serve those requests. When the ARC is full and there are L2ARC drives allocated to a ZFS pool, ZFS uses the L2ARC to serve the read requests that overflowed from the ARC. This reduces the use of slower hard drives and therefore increases system performance.

It also offloads any bandwidth that would be shared with the ZFS ZIL SLOG device, which I am also adding to mine, and would help you:
> 
In ZFS the SLOG will cache synchronous ZIL data before flushing to disk. When added to a ZFS array, this is essentially meant to be a high speed write cache. There is a lot more going on there with data stored in RAM, but this is a decent conceptual model for what is going on.

I used this calc: [https://wintelguy.com/zfs-calc.pl](https://wintelguy.com/zfs-calc.pl)

You have 32GB RAM. Usually, by rule-of-thumb, L2ARC should not be greater than 10 times the amount of RAM, which would be 320GB, but the SLOG calc's for 8x4TB drives using RAIDZ3 would be 0.6TB... So I would do a 512GB L2ARC, and 512GB SLOG.

Mine is a bit more breathing room on limits, as I have 128GB RAM... I can use 1TB caches.

---

### Post by #&amp;thj^% on 2023-04-19
> **MAFoElffen said:**
> As you have said and said is your mantra: "Life is too short to use slow computers"

RE: 
[https://www.ebay.com/itm/325614739010?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A19wIp10bmRa2IA0muPfHCTw18&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325614739010&targetid=1584571731043&device=c&mktype=&googleloc=9033423&poi=&campaignid=15275224983&mkgroupid=131097072938&rlsatarget=pla-1584571731043&abcId=9300697&merchantid=114727230&gclid=CjwKCAjwov6hBhBsEiwAvrvN6N9BFg86-hA8JduP20u2tJQnZEEuYpolgW4_Y_IqExjP2LnanstTQhoCvCkQAvD_BwE](https://www.ebay.com/itm/325614739010?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A19wIp10bmRa2IA0muPfHCTw18&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325614739010&targetid=1584571731043&device=c&mktype=&googleloc=9033423&poi=&campaignid=15275224983&mkgroupid=131097072938&rlsatarget=pla-1584571731043&abcId=9300697&merchantid=114727230&gclid=CjwKCAjwov6hBhBsEiwAvrvN6N9BFg86-hA8JduP20u2tJQnZEEuYpolgW4_Y_IqExjP2LnanstTQhoCvCkQAvD_BwE)

[https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675](https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675)

I think either of those would show quite a bit of difference with your baselines... Just to remove that bottleneck there. It's an investment that I think is worth it. This is one rare things that I think spending a little money will make a considerable worthwhile difference.

It would mean no changes in config (right now). Just pop the old card out and new card in. Retest the benchmarks and compare with your baseline.

+1 I believe i mentioned that in his other thread..and it seems cheap enough to play with.
No one asked and I have no ties to any of the vendors shown, but I'd go with this one: [https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675](https://www.ebay.com/itm/155421555013?_trkparms=amclksrc%3DITM%26aid%3D1110018%26algo%3DHOMESPLICE.COMPLISTINGS%26ao%3D1%26asc%3D248525%26meid%3D5fa06e5360224a1a8b367c8c399a6b0b%26pid%3D101196%26rk%3D4%26rkt%3D12%26sd%3D325614739010%26itm%3D155421555013%26pmt%3D1%26noa%3D0%26pg%3D2047675%26algv%3DPopularItemsWithSimpleRanker%26brand%3DLSI&_trksid=p2047675.c101196.m2219&amdata=cksum%3A1554215550135fa06e5360224a1a8b367c8c399a6b0b%7Cenc%3AAQAIAAAA8GOmCSQpkmvxUrVGPpSDVG%252FozIAfxJaYl2jGtITibHVRf3fcL9MU6n%252BCWEvGFLfvNrtRsYuR8D7WXVQZ7d5TRQq2PnD1bPlfQ2Jqi2szt9ELS8mHcUbDuby%252BmproFJCHF92IKBrYKoLpwfJHrEJxZkG0S59uzT3nx2tfdgSIRXEQQ%252BtDnUWyfpl1VHNt8nlSYxa0EUt%252BBFpQlLM2%252BgLtRzaQ8NBSS7e0ZoGBBFqPeH8Np5wLdq5kRWDjm0k5axclBBzwdkv9GnAdcfHsTjREDzHq0iGbFn6bdntv4NtY%252BITjw0qxkVI9Hl9FaCiM6bJq7g%253D%253D%7Campid%3APL_CLK%7Cclp%3A2047675)

---

### Post by MAFoElffen on 2023-04-19
LOL. That's why I linked that one. I used to have an IBM XServer with IBM ServerRAID hard RAID. Those cards were a PITA. I am assuming newer ServerRAID are a lot easier.

I had challenges where I had to boot from IBM's ServerRAID boot CD disks to do any configs on the SCSI drives. I then converted their RedHat GUI util's from RPM to Debian Packages to run on Ubuntu 10.04 LTS... Oh, the nightmares... LOL

---

### Post by papriak on 2023-04-20
Alrighty, I ordered one of the 9200-8i's from that listing and I'll look for my 500GB SSD this weekend.

While I wait, might there be a way to increase the efficiency of the current setup?

I'm thinking if 50MB/s is the speed of 1 drive, wouldn't the other 4 drives not being used for parity at the time make the speed close to 250MB/s if being written to in a round-robin pattern?

---

### Post by MAFoElffen on 2023-04-20
Yes... If there were no bottleneck at the HBA, then you might expect what they found here as what they found as benchmarks for different RAIDZ and RAID configs here: [https://calomel.org/zfs_raid_speed_capacity.html](https://calomel.org/zfs_raid_speed_capacity.html)

But another thing I remember you mentioning, it that the main job of the Server was being a Samba Share to 3 Windows machines and you were previously looking at the Windows File Manager widget to judge transfer speeds. Right?

Overall NTFS File shares are faster than using SMB network shares. Someone like TheFu can confirm that. He has used NTFS network shares for as long as I have know him.

As for other things... For my old server racks in-home, I used to use fiber backbones to do my backups. Logically, tweaking the networking between the machines may help with what your are doing with Network shares... But it may be complete overkill. 

With network Fileshares, you don't transfer big files to the client to be able to work on them and access them on the share. You deal with latency, read and writes on the share itself. Well, that all depends on what you are accessing with what application. But generally.

If you look at the link above, it mentions BSD Tuning and Optimization: [https://calomel.org/freebsd_network_tuning.html](https://calomel.org/freebsd_network_tuning.html)
You can Google and apply those same tuning tips to Ubuntu through the sysctl.conf...
[https://gist.github.com/maprangzth/093090eeba7775c10a277eda8dcd3e01](https://gist.github.com/maprangzth/093090eeba7775c10a277eda8dcd3e01)
[https://easyengine.io/tutorials/linux/sysctl-conf/](https://easyengine.io/tutorials/linux/sysctl-conf/)
[https://hostingultraso.com/help/ubuntu/tuning-tcp-stack-ubuntu](https://hostingultraso.com/help/ubuntu/tuning-tcp-stack-ubuntu)

---

### Post by papriak on 2023-04-20
> **MAFoElffen said:**
> Yes... If there were no bottleneck at the HBA, then you might expect what they found here as what they found as benchmarks for different RAIDZ and RAID configs here: [https://calomel.org/zfs_raid_speed_capacity.html](https://calomel.org/zfs_raid_speed_capacity.html)

The transfer rates in that link are about what I was expecting, yes.

I don't think my network is the issue though:  I installed 10Gbit NICs in my server and main Windows machine, and can get transfers over 1GB/s between NVMe SSDs.

Also I think I mentioned in the prior thread (I could be wrong) that my pool is getting 50MB/s transfers between it and the server's SSD.

---

### Post by MAFoElffen on 2023-04-21
You already took care of that then... Network wise.

I look at this:
```

 5x 4TB, raidz3 (raid7),        7.5 TB,  w=116MB/s , rw=45MB/s  , r=493MB/s 
11x 4TB, raidz3 (raid7),       30.2 TB,  w=552MB/s , rw=103MB/s , r=963MB/s 

```
Mathematically by those stat's and a possible algorithm would put your expected rates to be around 400MB/s... Even though your advertised drive stats's say 600MB/s(?) for each single drive.

Your's should be faster.

Right now, in the chassis, you are only getting around 60MB/s.
```

Run status group 0 (all jobs):
  WRITE: bw=62.1MiB/s (65.1MB/s), 62.1MiB/s-62.1MiB/s (65.1MB/s-65.1MB/s), io=3725MiB (3906MB), run=60003-60003msec

```
My datapool running the same test write test on HDD is running:
```

Run status group 0 (all jobs):
  WRITE: bw=524MiB/s (550MB/s), 524MiB/s-524MiB/s (550MB/s-550MB/s), io=10.0GiB (10.7GB), run=19537-19537msec

```
And yours ran with less data, for a longer time...

Dang. I guess we shall see after the HBA card arrives.

---

### Post by papriak on 2023-04-21
> **MAFoElffen said:**
> 
Mathematically by those stat's and a possible algorithm would put your expected rates to be around 400MB/s... Even though your advertised drive stats's say 600MB/s(?) for each single drive.

I think that was the SATA III interface speed.  The sheet claims sustained transfer rates are 171-183 MB/s depending on the model.

> Dang. I guess we shall see after the HBA card arrives.

Yep, we'll see.

---

### Post by MAFoElffen on 2023-05-01
Did your new HBA card come in yet? Patiently waiting to see how much that helped. I am curious to see the results.

So... I was tuning my datapool tonight to get some new benchmarks, and am posting them so you have some tips for yours.

I added the L2ARC and SLOG in that I had plans for... I wanted to show you the results of just that, so you can compare what kinds of increases of performance by just adding those cache devices, before I add in my new 4xNVme card for the replacement datapool (from HHD to RAIDz2 on NVMe)...

My old stats from my worst case test scenario (Post #6) using this code:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=randrw --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
was:
```

Run status group 0 (all jobs):
   READ: bw=133KiB/s (136kB/s), 133KiB/s-133KiB/s (136kB/s-136kB/s), io=7968KiB (8159kB), run=60011-60011msec
  WRITE: bw=140KiB/s (144kB/s), 140KiB/s-140KiB/s (144kB/s-144kB/s), io=8420KiB (8622kB), run=60011-60011msec

```
Now with limiting my ARC to between 2GB (minimum) to 32GB (maximum), adding both SLOG and DL2ARC devices (500GB each):
```

Run status group 0 (all jobs):
   READ: bw=1809KiB/s (1853kB/s), 1809KiB/s-1809KiB/s (1853kB/s-1853kB/s), io=106MiB (111MB), run=60001-60001msec
  WRITE: bw=1808KiB/s (1851kB/s), 1808KiB/s-1808KiB/s (1851kB/s-1851kB/s), io=106MiB (111MB), run=60001-60001msec

```
So an increase in performance of 13 times faster, just by adding a SLOG Device and a L2ARC device of 500GB's each. off-loading those services to other bandwidth on dedicated devices helps out greatly, as you can see from the test results.

The newer HBA I ordered comes in a little over a week. I'll post the results of that when it comes in...

EDIT: I forgot the explanations, didn't I? 
L2ARC device cache increases performance on the read. SLOG cache increases the write performance. But adding a dedicated SLOG device... SLOG is by default just in RAM, adding a SLOG device adds it being to disk, which decreases the risk of loosing those transactions in case of a power outage.

---

### Post by papriak on 2023-05-01
> **MAFoElffen said:**
> Did your new HBA card come in yet? Patiently waiting to see how much that helped. I am curious to see the results.

It did, but the SSD containing Ubuntu is booting to a recovery menu and I don't know how to proceed.

That really killed the mood, I apologize for making you wait.



I should have time tomorrow to reload and get back to you.

---

### Post by MAFoElffen on 2023-05-01
Hmmm... You know we can help answer questions to help help with that if necessary.

Realistically, I don't think I posted my stats from these twoo commands, which was for just a read, and just a write:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
Which mine came back now with these benchmarks:
```

Run status group 0 (all jobs):
   READ: bw=5845MiB/s (6129MB/s), 5845MiB/s-5845MiB/s (6129MB/s-6129MB/s), io=10.0GiB (10.7GB), run=1752-1752msec
Run status group 0 (all jobs):
  WRITE: bw=615MiB/s (645MB/s), 615MiB/s-615MiB/s (645MB/s-645MB/s), io=10.0GiB (10.7GB), run=16660-16660msec

```
These are coming back with 3-4 times faster, than before...

If you can, run two sets of benchmarks. One with just the change in the HBA card, and one after adding the L2ARC cache. 

Did I add the command to add the L2ARC cache? If I didn't
```

sudo zpool add [pool_name] cache /dev/disk/by-id/[disk_name-partition_number]

```
For example, for mine was
```

sudo zpool add datapool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part1

```

---

### Post by papriak on 2023-05-01
I think it would be easier just to start over, experimenting as I went left the old install with some vestigial programs and possible remnants.

I'll definitely work on the system tomorrow and upload the results.

---

### Post by #&amp;thj^% on 2023-05-01
I'm still here. :-$
Can't wait to see your first results.

---

### Post by papriak on 2023-05-01
> **1fallen said:**
> I'm still here. :-$
Can't wait to see your first results.

Hello again.  :)

Ubuntu is reinstalled, and the pool has been imported.  I'm currently running a scrub to be safe, it should finish shortly before I go to bed.

I'll swap out the card and post the new speeds tomorrow.

---

### Post by papriak on 2023-05-02
> **MAFoElffen said:**
> Hmmm... You know we can help answer questions to help help with that if necessary.

Realistically, I don't think I posted my stats from these twoo commands, which was for just a read, and just a write:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
Which mine came back now with these benchmarks:
```

Run status group 0 (all jobs):
   READ: bw=5845MiB/s (6129MB/s), 5845MiB/s-5845MiB/s (6129MB/s-6129MB/s), io=10.0GiB (10.7GB), run=1752-1752msec
Run status group 0 (all jobs):
  WRITE: bw=615MiB/s (645MB/s), 615MiB/s-615MiB/s (645MB/s-645MB/s), io=10.0GiB (10.7GB), run=16660-16660msec

```
These are coming back with 3-4 times faster, than before...

If you can, run two sets of benchmarks. One with just the change in the HBA card, and one after adding the L2ARC cache. 

Did I add the command to add the L2ARC cache? If I didn't
```

sudo zpool add [pool_name] cache /dev/disk/by-id/[disk_name-partition_number]

```
For example, for mine was
```

sudo zpool add datapool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part1

```

New card results without cache SSDs:

Read:

```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=16354: Tue May  2 17:01:29 2023
  read: IOPS=109, BW=109MiB/s (114MB/s)(6545MiB/60001msec)
    slat (usec): min=4378, max=71960, avg=9161.33, stdev=6346.08
    clat (usec): min=2, max=651825, avg=281119.34, stdev=193717.46
     lat (msec): min=4, max=710, avg=290.28, stdev=199.93
    clat percentiles (msec):
     |  1.00th=[   88],  5.00th=[  150], 10.00th=[  153], 20.00th=[  153],
     | 30.00th=[  155], 40.00th=[  155], 50.00th=[  155], 60.00th=[  157],
     | 70.00th=[  542], 80.00th=[  558], 90.00th=[  567], 95.00th=[  600],
     | 99.00th=[  609], 99.50th=[  609], 99.90th=[  634], 99.95th=[  642],
     | 99.99th=[  651]
   bw (  KiB/s): min=34816, max=253952, per=99.69%, avg=111355.66, stdev=73335.44, samples=118
   iops        : min=   34, max=  248, avg=108.75, stdev=71.62, samples=118
  lat (usec)   : 4=0.03%, 10=0.03%
  lat (msec)   : 10=0.09%, 20=0.14%, 50=0.32%, 100=0.53%, 250=67.87%
  lat (msec)   : 500=0.23%, 750=30.76%
  cpu          : usr=0.08%, sys=99.67%, ctx=685, majf=0, minf=8207
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.5%, 16=1.0%, 32=98.1%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=6545,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=109MiB/s (114MB/s), 109MiB/s-109MiB/s (114MB/s-114MB/s), io=6545MiB (6863MB), run=60001-60001msec
```

Write:

```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=640877: Tue May  2 17:03:28 2023
  write: IOPS=55, BW=55.8MiB/s (58.5MB/s)(3349MiB/60037msec); 0 zone resets
    slat (msec): min=9, max=132, avg=17.92, stdev=10.95
    clat (usec): min=9, max=2135.7k, avg=550823.33, stdev=294729.12
     lat (msec): min=15, max=2209, avg=568.74, stdev=303.50
    clat percentiles (msec):
     |  1.00th=[  296],  5.00th=[  342], 10.00th=[  347], 20.00th=[  418],
     | 30.00th=[  451], 40.00th=[  481], 50.00th=[  510], 60.00th=[  542],
     | 70.00th=[  558], 80.00th=[  584], 90.00th=[  609], 95.00th=[  701],
     | 99.00th=[ 2072], 99.50th=[ 2106], 99.90th=[ 2140], 99.95th=[ 2140],
     | 99.99th=[ 2140]
   bw (  KiB/s): min= 8192, max=118784, per=99.91%, avg=57072.20, stdev=21150.72, samples=119
   iops        : min=    8, max=  116, avg=55.70, stdev=20.67, samples=119
  lat (usec)   : 10=0.03%, 20=0.03%
  lat (msec)   : 20=0.03%, 50=0.09%, 100=0.09%, 250=0.33%, 500=46.31%
  lat (msec)   : 750=48.55%, 1000=0.30%, 2000=2.51%, >=2000=1.73%
  cpu          : usr=0.30%, sys=89.42%, ctx=59300, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.5%, 16=1.0%, 32=98.1%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3349,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=55.8MiB/s (58.5MB/s), 55.8MiB/s-55.8MiB/s (58.5MB/s-58.5MB/s), io=3349MiB (3512MB), run=60037-60037msec

```

I'll install the SSDs and run the tests again in a few hours.

---

### Post by #&amp;thj^% on 2023-05-02
Interesting, I'll wait for MAFoElffen to offer up some more suggestions. (Too many cooks spoil the recipe)
You should have better write speed here:
```
zpool status
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  7e715b37-98cb-114c-b867-41fcb612b495  ONLINE       0     0     0

errors: No known data errors

  pool: pool3
 state: ONLINE
config:

	NAME         STATE     READ WRITE CKSUM
	pool3        ONLINE       0     0     0
	  nvme1n1p4  ONLINE       0     0     0

errors: No known data errors

  pool: pool4
 state: ONLINE
config:

	NAME         STATE     READ WRITE CKSUM
	pool4        ONLINE       0     0     0
	  nvme0n1p2  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  a08f00aa-b297-0046-9fce-3493550eeb22  ONLINE       0     0     0

errors: No known data errors


```
Read speed:
```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.33
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=0): [f(1)][100.0%][r=2509MiB/s][r=2509 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=939709: Tue May  2 11:09:17 2023
  read: IOPS=2066, BW=2066MiB/s (2167MB/s)(10.0GiB/4956msec)
    slat (usec): min=275, max=10012, avg=481.84, stdev=423.92
    clat (usec): min=2, max=79163, avg=14782.55, stdev=12403.92
     lat (usec): min=369, max=89176, avg=15264.40, stdev=12811.32
    clat percentiles (usec):
     |  1.00th=[ 7504],  5.00th=[11731], 10.00th=[11731], 20.00th=[11731],
     | 30.00th=[11731], 40.00th=[11731], 50.00th=[11731], 60.00th=[11863],
     | 70.00th=[11863], 80.00th=[12125], 90.00th=[12387], 95.00th=[35390],
     | 99.00th=[77071], 99.50th=[78119], 99.90th=[78119], 99.95th=[78119],
     | 99.99th=[79168]
   bw (  MiB/s): min=  329, max= 2634, per=97.04%, avg=2005.04, stdev=963.10, samples=9
   iops        : min=  329, max= 2634, avg=2005.00, stdev=963.17, samples=9
  lat (usec)   : 4=0.05%, 500=0.05%, 1000=0.05%
  lat (msec)   : 2=0.15%, 4=0.24%, 10=0.78%, 20=92.34%, 50=1.85%
  lat (msec)   : 100=4.49%
  cpu          : usr=0.40%, sys=82.79%, ctx=610, majf=13, minf=8202
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2066MiB/s (2167MB/s), 2066MiB/s-2066MiB/s (2167MB/s-2167MB/s), io=10.0GiB (10.7GB), run=4956-4956msec


```
Write Speed:
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.33
Starting 1 process
Jobs: 1 (f=1): [W(1)][30.4%][w=383MiB/s][w=383 IOPS][eta 00m:16s]
Jobs: 1 (f=1): [W(1)][54.2%][w=377MiB/s][w=377 IOPS][eta 00m:11s] 
Jobs: 1 (f=1): [W(1)][65.5%][w=235MiB/s][w=235 IOPS][eta 00m:10s] 
Jobs: 1 (f=1): [W(1)][80.6%][w=261MiB/s][w=261 IOPS][eta 00m:06s] 
Jobs: 1 (f=1): [W(1)][91.2%][w=244MiB/s][w=244 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][97.4%][eta 00m:01s]                         
Jobs: 1 (f=1): [W(1)][97.5%][eta 00m:01s] 
TEST: (groupid=0, jobs=1): err= 0: pid=945020: Tue May  2 11:11:34 2023
  write: IOPS=259, BW=260MiB/s (272MB/s)(10.0GiB/39436msec); 0 zone resets
    slat (usec): min=244, max=57273, avg=3268.87, stdev=1995.39
    clat (usec): min=2, max=6007.1k, avg=118514.51, stdev=326672.99
     lat (usec): min=271, max=6011.4k, avg=121783.38, stdev=327053.20
    clat percentiles (msec):
     |  1.00th=[    9],  5.00th=[   17], 10.00th=[   69], 20.00th=[   80],
     | 30.00th=[   81], 40.00th=[   82], 50.00th=[   83], 60.00th=[  104],
     | 70.00th=[  117], 80.00th=[  125], 90.00th=[  140], 95.00th=[  167],
     | 99.00th=[  443], 99.50th=[  518], 99.90th=[ 5940], 99.95th=[ 6007],
     | 99.99th=[ 6007]
   bw (  KiB/s): min=61440, max=1323008, per=100.00%, avg=304724.06, stdev=160796.18, samples=67
   iops        : min=   60, max= 1292, avg=297.58, stdev=157.03, samples=67
  lat (usec)   : 4=0.02%, 10=0.02%, 20=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.03%, 4=0.09%, 10=2.29%, 20=4.70%, 50=1.72%
  lat (msec)   : 100=50.65%, 250=37.57%, 500=2.26%, 750=0.32%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=6011.0M, max=6011.0M, avg=6010967510.00, stdev= 0.00
    sync percentiles (msec):
     |  1.00th=[ 6007],  5.00th=[ 6007], 10.00th=[ 6007], 20.00th=[ 6007],
     | 30.00th=[ 6007], 40.00th=[ 6007], 50.00th=[ 6007], 60.00th=[ 6007],
     | 70.00th=[ 6007], 80.00th=[ 6007], 90.00th=[ 6007], 95.00th=[ 6007],
     | 99.00th=[ 6007], 99.50th=[ 6007], 99.90th=[ 6007], 99.95th=[ 6007],
     | 99.99th=[ 6007]
  cpu          : usr=1.17%, sys=10.35%, ctx=80040, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=260MiB/s (272MB/s), 260MiB/s-260MiB/s (272MB/s-272MB/s), io=10.0GiB (10.7GB), run=39436-39436msec


```
For the record the only controller is my MB.

---

### Post by papriak on 2023-05-02
> **1fallen said:**
> Interesting, I'll wait for MAFoElffen to offer up some more suggestions. (Too many cooks spoil the recipe)
You should have better write speed here

That's what I thought.

What's the next step?  Should I install the SSDs, or figure out what's causing the pool to run so slowly?

---

### Post by MAFoElffen on 2023-05-03
> **papriak said:**
> That's what I thought.

What's the next step?  Should I install the SSDs, or figure out what's causing the pool to run so slowly?
Dang it, Your read speed increased a minute amount, and your write speed actually got "worse".

Old Stat's:
```

  read: IOPS=103, BW=103MiB/s (108MB/s)(6197MiB/60004msec)
   READ: bw=103MiB/s (108MB/s), 103MiB/s-103MiB/s (108MB/s-108MB/s), io=6197MiB (6498MB), run=60004-60004msec
  write: IOPS=62, BW=62.1MiB/s (65.1MB/s)(3725MiB/60003msec); 0 zone resets
  WRITE: bw=62.1MiB/s (65.1MB/s), 62.1MiB/s-62.1MiB/s (65.1MB/s-65.1MB/s), io=3725MiB (3906MB), run=60003-60003msec

```
New Stat's:
```

  read: IOPS=109, BW=109MiB/s (114MB/s)(6545MiB/60001msec)
   READ: bw=109MiB/s (114MB/s), 109MiB/s-109MiB/s (114MB/s-114MB/s), io=6545MiB (6863MB), run=60001-60001msec
  write: IOPS=55, BW=55.8MiB/s (58.5MB/s)(3349MiB/60037msec); 0 zone resets
  WRITE: bw=55.8MiB/s (58.5MB/s), 55.8MiB/s-55.8MiB/s (58.5MB/s-58.5MB/s), io=3349MiB (3512MB), run=60037-60037msec

```

The HHD drives you have are 7200 rpm drives. Mine are 5600's and actually running faster IOPS?

Something is wrong there. Your problem is not ARC and I don't think concentrating on adding a L2ARC will help, because that cache's reads.

You have the SSD to use as cache, I would install as SLOG, which is write cache.
```

sudo zpool add -f kpool log /dev/disk/by-id/[disk_name]-[partition]
# Example
sudo zpool add -f kpool log /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part1

```
That is going to improve what you have. Though there is still something going on.

Also please post the results of (replace with your pool name and dataset name)
```

for i in sync recordsize compression compressratio atime xattr logbias dedup acltype copies volblocksize; do sudo zfs get $i [pool_name]/[dataset_name]; done | grep -v NAME
sudo zpool get ashift,feature@async_destroy,feature@empty_bpobj,feature@lz4_compress [pool_name]
sudo zpool iostat [pool_name]

```
Here is my stats so we can compare notes:
```

mafoelffen@Mikes-B460M:/data$ for i in sync recordsize compression compressratio atime xattr logbias dedup acltype copies volblocksize; do sudo zfs get $i datapool/DATA; done | grep -v NAME
datapool/DATA  sync      standard  default
datapool/DATA  recordsize  128K     default
datapool/DATA  compression  lz4             inherited from datapool
datapool/DATA  compressratio  1.25x  -
datapool/DATA  atime     off    inherited from datapool
datapool/DATA  xattr     sa     inherited from datapool
datapool/DATA  logbias   latency     default
datapool/DATA  dedup     off            default
datapool/DATA  acltype   posix     inherited from datapool
datapool/DATA  copies    1       default
datapool/DATA  volblocksize  -         -
mafoelffen@Mikes-B460M:/data$ sudo zpool get ashift,feature@async_destroy,feature@empty_bpobj,feature@lz4_compress datapool
NAME      PROPERTY               VALUE                  SOURCE
datapool  ashift                 12                     local
datapool  feature@async_destroy  enabled                local
datapool  feature@empty_bpobj    active                 local
datapool  feature@lz4_compress   active                 local
mafoelffen@Mikes-B460M:/data$ sudo zpool iostat datapool
              capacity     operations     bandwidth 
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
datapool     744G  2.90T      0      2  6.65K   215K

```

---

### Post by papriak on 2023-05-03
> **MAFoElffen said:**
> Dang it, Your read speed increased a minute amount, and your write speed actually got "worse".

There is still something going on.

Also please post the results of (replace with your pool name and dataset name)
```

for i in sync recordsize compression compressratio atime xattr logbias dedup acltype copies volblocksize; do sudo zfs get $i [pool_name]/[dataset_name]; done | grep -v NAME
sudo zpool get ashift,feature@async_destroy,feature@empty_bpobj,feature@lz4_compress [pool_name]
sudo zpool iostat [pool_name]

```


I'd like to solve the slowness before adding write cache, if that's okay.

Here's the results of your code:

Line 1:

```
Pool/Backups  sync      standard  default
Pool/Backups  recordsize  512      inherited from Pool
Pool/Backups  compression  off             inherited from Pool
Pool/Backups  compressratio  1.00x  -
Pool/Backups  atime     on     default
Pool/Backups  xattr     sa     inherited from Pool
Pool/Backups  logbias   latency     default
Pool/Backups  dedup     off            default
Pool/Backups  acltype   posix     inherited from Pool
Pool/Backups  copies    1       default
Pool/Backups  volblocksize  -         -

```

Line 2:

```
NAME  PROPERTY               VALUE                  SOURCE
Pool  ashift                 9                      local
Pool  feature@async_destroy  enabled                local
Pool  feature@empty_bpobj    active                 local
Pool  feature@lz4_compress   active                 local

```

Line 3:

```
              capacity     operations     bandwidth 
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
Pool         665G  28.5T      6      8   243K  9.98K

```

---

### Post by #&amp;thj^% on 2023-05-03
> **papriak said:**
> 
Line 3:

```
              capacity     operations     bandwidth 
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
Pool         665G  28.5T      6      8   243K  9.98K

```

Possible reason on this disk.

These are the first things I look at for slow write speeds
NetWork card (Ethernet)
Drives themselfs (SSD, Spinning HD, Raid Devices)
Is the pool nearly full? ZFS goes into a slower allocation mode when this happens. 
Write on "tank"
```
me on Wed May 03 at 10:15 AM in /tank branch: (HEAD) 
>> sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.33
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][50.0%][w=358MiB/s][w=358 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][76.5%][w=469MiB/s][w=469 IOPS][eta 00m:04s] 
Jobs: 1 (f=1): [W(1)][95.0%][w=334MiB/s][w=334 IOPS][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=212MiB/s][w=212 IOPS][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=347164: Wed May  3 10:16:48 2023
  write: IOPS=481, BW=481MiB/s (505MB/s)(10.0GiB/21269msec); 0 zone resets
    slat (usec): min=242, max=34230, avg=1976.08, stdev=1219.64
    clat (usec): min=4, max=977100, avg=63834.54, stdev=59873.41
     lat (usec): min=413, max=978966, avg=65810.62, stdev=60500.29
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   15], 20.00th=[   18],
     | 30.00th=[   45], 40.00th=[   58], 50.00th=[   63], 60.00th=[   69],
     | 70.00th=[   79], 80.00th=[   90], 90.00th=[  107], 95.00th=[  122],
     | 99.00th=[  155], 99.50th=[  159], 99.90th=[  961], 99.95th=[  969],
     | 99.99th=[  978]
   bw (  KiB/s): min=219136, max=1757184, per=100.00%, avg=497963.71, stdev=358947.73, samples=41
   iops        : min=  214, max= 1716, avg=486.29, stdev=350.53, samples=41
  lat (usec)   : 10=0.03%, 20=0.02%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.06%, 4=0.11%, 10=0.74%, 20=22.22%, 50=8.98%
  lat (msec)   : 100=54.75%, 250=12.76%, 1000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=978605k, max=978605k, avg=978605142.00, stdev= 0.00
    sync percentiles (msec):
     |  1.00th=[  978],  5.00th=[  978], 10.00th=[  978], 20.00th=[  978],
     | 30.00th=[  978], 40.00th=[  978], 50.00th=[  978], 60.00th=[  978],
     | 70.00th=[  978], 80.00th=[  978], 90.00th=[  978], 95.00th=[  978],
     | 99.00th=[  978], 99.50th=[  978], 99.90th=[  978], 99.95th=[  978],
     | 99.99th=[  978]
  cpu          : usr=2.91%, sys=21.85%, ctx=60540, majf=12, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=481MiB/s (505MB/s), 481MiB/s-481MiB/s (505MB/s-505MB/s), io=10.0GiB (10.7GB), run=21269-21269msec


```
What is connected as now this moment?   (Pools or Drives)
I think Mike has already suggested pulling Drives offline one at time? (I haven't seen thos results yet)
For Pool3:
```
me on Wed May 03 at 10:22 AM in /pool3 branch: (HEAD) 

```
```
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][100.0%][w=1615MiB/s][w=1615 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=376551: Wed May  3 10:22:56 2023
  write: IOPS=1580, BW=1580MiB/s (1657MB/s)(10.0GiB/6480msec); 0 zone resets
    slat (usec): min=251, max=9784, avg=614.85, stdev=512.59
    clat (usec): min=4, max=76373, avg=19501.62, stdev=9978.35
     lat (usec): min=291, max=77244, avg=20116.47, stdev=10157.26
    clat percentiles (usec):
     |  1.00th=[ 9110],  5.00th=[ 9503], 10.00th=[ 9765], 20.00th=[10028],
     | 30.00th=[10421], 40.00th=[14353], 50.00th=[19268], 60.00th=[21365],
     | 70.00th=[22676], 80.00th=[27132], 90.00th=[33817], 95.00th=[36963],
     | 99.00th=[47449], 99.50th=[63177], 99.90th=[72877], 99.95th=[74974],
     | 99.99th=[76022]
   bw (  MiB/s): min= 1488, max= 1646, per=100.00%, avg=1585.98, stdev=45.20, samples=12
   iops        : min= 1488, max= 1646, avg=1585.83, stdev=45.16, samples=12
  lat (usec)   : 10=0.05%, 500=0.03%, 750=0.04%, 1000=0.02%
  lat (msec)   : 2=0.12%, 4=0.20%, 10=19.15%, 20=33.14%, 50=46.44%
  lat (msec)   : 100=0.82%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=76928k, max=76928k, avg=76928438.00, stdev= 0.00
    sync percentiles (usec):
     |  1.00th=[77071],  5.00th=[77071], 10.00th=[77071], 20.00th=[77071],
     | 30.00th=[77071], 40.00th=[77071], 50.00th=[77071], 60.00th=[77071],
     | 70.00th=[77071], 80.00th=[77071], 90.00th=[77071], 95.00th=[77071],
     | 99.00th=[77071], 99.50th=[77071], 99.90th=[77071], 99.95th=[77071],
     | 99.99th=[77071]
  cpu          : usr=10.16%, sys=84.10%, ctx=2165, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1580MiB/s (1657MB/s), 1580MiB/s-1580MiB/s (1657MB/s-1657MB/s), io=10.0GiB (10.7GB), run=6480-6480msec


```
This one above is my fastest Drive, 
```

[code] WRITE: bw=1580MiB/s (1657MB/s), 1580MiB/s-1580MiB/s (1657MB/s-1657MB/s), io=10.0GiB (10.7GB), run=6480-6480msec

```
Now for Tank Drive:
```
 WRITE: bw=481MiB/s (505MB/s), 481MiB/s-481MiB/s (505MB/s-505MB/s), io=10.0GiB (10.7GB), run=21269-21269msec
```
Both Drives are single pools on SSD's (Just for this case use) but you can see speed diffs.
```
inxi -p | grep tank 
  ID-8: /tank size: 230.62 GiB used: 2 GiB (0.9%) fs: zfs logical: tank

inxi -p | grep pool3
  ID-5: /pool3 size: 228.69 GiB used: 2 GiB (0.9%) fs: zfs logical: pool3

```
If only i could be a Fly on the Wall....

---

### Post by papriak on 2023-05-03
> **1fallen said:**
> Possible reason on this disk.

These are the first things I look at for slow write speeds
NetWork card (Ethernet)
Drives themselfs (SSD, Spinning HD, Raid Devices)
Is the pool nearly full? ZFS goes into a slower allocation mode when this happens. 


I'm not transferring data between machines at this time, but when I do it's over a 10G connection that works great between SSDs.

As for allocation, I'm using 665GB out of 28.46TB.  Unless you mean I should lower the partition size?

What are the code(s) to turn off a single disk before running the tests again?

---

### Post by #&amp;thj^% on 2023-05-03
Here's a great source: [https://openzfs.github.io/openzfs-docs/man/8/zpool-offline.8.html](https://openzfs.github.io/openzfs-docs/man/8/zpool-offline.8.html)
On the left is kind of an Index.
And this I'm up in the air over>>"As for allocation, I'm using 665GB out of 28.46TB. Unless you mean I should lower the partition size?
"

---

### Post by papriak on 2023-05-03
> **1fallen said:**
> Here's a great source: [https://openzfs.github.io/openzfs-docs/man/8/zpool-offline.8.html](https://openzfs.github.io/openzfs-docs/man/8/zpool-offline.8.html)
On the left is kind of an Index.
And this I'm up in the air over>>"As for allocation, I'm using 665GB out of 28.46TB. Unless you mean I should lower the partition size?
"

I meant that the pool is nowhere near full, but perhaps I can reduce the logical volume size.

---

### Post by #&amp;thj^% on 2023-05-03
> **papriak said:**
> I meant that the pool is nowhere near full, but perhaps I can reduce the logical volume size.
We might be talking past each other now, I wouldn't touch that yet, kind of a last resort thing. :)
I would simply try detaching drives for your test results see if we can narrow down a long list of trouble shooting first.

---

### Post by papriak on 2023-05-03
> **1fallen said:**
> We might be talking past each other now, I wouldn't touch that yet, kind of a last resort thing. :)
I would simply try detaching drives for your test results see if we can narrow down a long list of trouble shooting first.

Sounds good to me.  I'll try detaching one at a time and see what happens.

---

### Post by #&amp;thj^% on 2023-05-03
Just a Heads Up, I'll be offline for an Hour or so.
It's Back-Up Day at work I need to be present.

---

### Post by papriak on 2023-05-03
Question:  Won't offline-ing the disks make the pool slower?

---

### Post by MAFoElffen on 2023-05-03
Here's the dirt:
```

NAME           PROPERTY       VALUE(1)   VALUE(2)

datapool/DATA  sync           standard   standard
datapool/DATA  recordsize     128K       [COLOR=#ff0000]512[/COLOR]
datapool/DATA  compression    lz4        [COLOR=#ff0000]off[/COLOR]
datapool/DATA  compressratio  1.25x      1.00x
datapool/DATA  atime          off        on
datapool/DATA  xattr          sa         sa
datapool/DATA  logbias        latency    latency
datapool/DATA  dedup          off        off
datapool/DATA  acltype        posix      posix
datapool/DATA  copies         1          1
datapool/DATA  volblocksize   -          

Pool  ashift                  12         [COLOR=#ff0000]9[/COLOR]
Pool  feature@async_destroy   enabled    enabled
Pool  feature@empty_bpobj     active     active
Pool  feature@lz4_compress    active     active

              capacity     operations     bandwidth 
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
datapool(1)  744G  2.90T      0      2  6.65K   215K
Pool(2)      665G  28.5T      6      8   243K  [COLOR=#ff8c00]9.98K[/COLOR]

```
What I see is two things ([COLOR=#ff0000]highltighted in red[/COLOR]), resulting in poor write speeds [COLOR=#ff8c00](highlighted in orange)[/COLOR]...

I was suspecting the record size was wrong. It is... You can change recordsize, with a bot of work. The recordsize is set in the dataset. You reset the recordsize to the new size, move the data out of the dataset. Then rewrite it back to the dataset to the new record size. Rule of thumb- If the job is databases, then you tune the record size to 16k. KVM VM's do well with being set to 64K, because of the way QCOW2 files are stored. Th default setting is 128K, which for me is a happy medium. If streaming movies from a media player, then you set the record size to 1M. [COLOR=#ff0000]Yours is set to 512Bytes. [/COLOR]Another rule is that file block size should not be larger than the recordsize, but can be smaller. So setting it larger is not much of a performance hit, but setting it too small is very much of a performance hit. 

 When I create this new pool and it's datasets, the sector size is 4K,  with ashift set to 13. It is purely for KVM, so I am going to tune it just for that.

But your's has a deeper problem. Under the recordsize, in the pool, the sector size is way too small. The pool async setting is what deals with sector size. Your pool async is set to 9. Both my async and 1fallen's are set to 12. Why, intitially because that is what OpenZFS recommended to us in pool declares.

Even though your drive's spec's say it is 512 bytes, it is is suspect that it falls into the lied about category to be compliant with Windows... Let me quote OpenZFS developer Matt Ahrens, "it's really complicated."

This is a good read for you (where that quote is from): [https://arstechnica.com/information-technology/2020/05/zfs-101-understanding-zfs-storage-and-performance/](https://arstechnica.com/information-technology/2020/05/zfs-101-understanding-zfs-storage-and-performance/) 

It is a very good article, that will help you understand ZFS and how it f you go down to the "Sectors" section, please read the whole section. Here is snips from it that I feel pertain to your problem:
> 
This means that a ZFS admin is strongly advised to be aware of the actual sector size of his or her devices, and manually set ashift accordingly. If ashift is set too low, an astronomical read/write amplification penalty is incurred&#8212;writing a 512 byte "sectors" to a 4KiB real sector means having to write the first "sector", then read the 4KiB sector, modify it with the second 512 byte "sector", write it back out to a *new* 4KiB sector, and so forth, for every single write.

In real world terms, this amplification penalty hits a Samsung EVO SSD&#8212;which should have ashift=13, but lies about its sector size and therefore defaults to ashift=9 if not overridden by a savvy admin&#8212;hard enough to make it appear slower than a conventional rust disk.

By contrast, there is virtually no penalty to setting ashift too high. There is no real performance penalty, and slack space increases are infinitesimal (or zero, with compression enabled). We strongly recommend even disks that really do use 512 byte sectors should be set ashift=12 or even ashift=13 for future-proofing.

Unfortunately, ashift is not a setting that can be changed with a set coomand. Once 'set" in the intitial pool declare, It is considered immutable, and is that setting for the life of the pool. To change it the pool has to be destroyed and declared with the new setting... So you would have to start over to change that.

The other thing noted is to turn compression back on. I know that article says the performance having it on or off is not seen. (By those words, it wouldn't hurt to have it turned on. LOL) And this point changes depending on who you talk to. But by my benchmarks, it does make a noticeable difference. Most people think that turning compression off will make their pools faster, because they think that there will be less CPU overhead involved in the compression process. In reality, from my tests, it gets a performance hit making it slower, because with compression turned on, it runs faster because there is less data (in size) to move around and write.That is what I see from my tests. It is a balance and you have to play with it to see what works best for your hardware and what you do. You can use different compression methods to find out what works best for you. For me, I'm using lz4.

That is what I see from your results. Sorry for the news. It seems you have some work ahead. It will just involve a time investment to make those changes. 

I'm thinking if you get those changes done, and rerun your benchmarks, if it improves your I/O problem, then partitioning your SSD to two partitions, using one for SLOG and the other for L2ARC, might get you into the 400MiB/S to 500MiB/S range. (which is about 250% better than the vdev base drive spec's). That is optimistic. Closer might be 300-400. It might limit it having it on the same cable, but an SSD can write to multiple places without having to move anything... LOL. There's nothing that says it can't be on the same drive. It would just have more bandwidth being on separate drives.

---

### Post by #&amp;thj^% on 2023-05-03
Yep now that you put it right there in plain view.
Nicely suggested MAFoElffen.
I have to hand it to the OP (papriak) for his staying power. =d>

---

### Post by papriak on 2023-05-03
The pool has nothing new on it since I made the backup for the previous thread, so I have nothing to lose by destroying the pool and being more specific when recreating it.

I've offloaded the video streaming to an SSD on a Raspberry Pi 4 (Tough to beat those for silence and space savings) so the server is now purely for storing backups.  Specifically, I'll be storing Windows system images, the backups of my movies, and important documents on it.  What settings might you advise for max read/write speeds for those?

I had assumed that disabling compression would make for less overhead, but I can't argue that writing smaller files takes less drive time and the CPU time would be negligible.



And for what it's worth, the pool's write speeds were all about 60MB/s, and I got 200MB/s read speeds except for when /dev/sda was offlined:  The pool got 50MB/s read speeds without it.

Should I bother swapping out that drive with my spare, or is that kind of performance hit typical of removing the first device?

---

### Post by papriak on 2023-05-03
> **1fallen said:**
> I have to hand it to the OP (papriak) for his staying power. =d>

*takes a bow*  :P

---

### Post by MAFoElffen on 2023-05-03
> **papriak said:**
> Should I bother swapping out that drive with my spare, or is that kind of performance hit typical of removing the first device?
Which drive are we talking about? For what with what?
> **papriak said:**
> What settings might you advise for max read/write speeds for those?
Yes... I had other things to do today, but have been thinking about this...

For the specifics to ID the disks, remember the specific ID's from the last thread... You took care of that, but didn't post the specificcs of their names.
```

sudo zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl \
    -O xattr=sa \
    -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off \
    -O mountpoint=/Pool \
    Pool1 raidz3 \
    /dev/disk/by-id/disk1-part1 \
    /dev/disk/by-id/disk2-part1 \
    /dev/disk/by-id/disk3-part1 \
    /dev/disk/by-id/disk4-part1 \
    /dev/disk/by-id/disk5-part1 \
    /dev/disk/by-id/disk6-part1 \
    /dev/disk/by-id/disk7-part1 \
    /dev/disk/by-id/disk8-part1 \
    /dev/disk/by-id/disk9-part1

sudo zfs create \
    -o canmount=off \
    -o mountpoint=/Pool \
    Pool1/DATA

sudo zfs create \
    -o sharesmb=on \
    -o canmount=on \
    -o mountpoint=/Pool \
    Pool1/DATA/ubuntu_2204

```

---

### Post by papriak on 2023-05-03
> **MAFoElffen said:**
> Which drive are we talking about? For what with what?

I was referring to /dev/sda, I bought 9 drives in case one went bad.

> Yes... I had other things to do today, but have been thinking about this...

I greatly appreciate you taking time to assist me again.



I've recreated the pool without SSDs.

New read speed:
```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=16128: Thu May  4 03:22:41 2023
  read: IOPS=4753, BW=4754MiB/s (4985MB/s)(10.0GiB/2154msec)
    slat (usec): min=192, max=968, avg=208.42, stdev=25.17
    clat (usec): min=2, max=18503, avg=6450.56, stdev=653.01
     lat (usec): min=200, max=19473, avg=6659.23, stdev=668.23
    clat percentiles (usec):
     |  1.00th=[ 4178],  5.00th=[ 6390], 10.00th=[ 6456], 20.00th=[ 6456],
     | 30.00th=[ 6456], 40.00th=[ 6456], 50.00th=[ 6456], 60.00th=[ 6456],
     | 70.00th=[ 6456], 80.00th=[ 6521], 90.00th=[ 6521], 95.00th=[ 6521],
     | 99.00th=[ 7111], 99.50th=[ 8455], 99.90th=[15270], 99.95th=[16909],
     | 99.99th=[18220]
   bw (  MiB/s): min= 4562, max= 4800, per=99.64%, avg=4737.00, stdev=116.78, samples=4
   iops        : min= 4562, max= 4800, avg=4737.00, stdev=116.78, samples=4
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.24%, 4=0.49%, 10=98.76%, 20=0.26%
  cpu          : usr=0.51%, sys=99.35%, ctx=9, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4754MiB/s (4985MB/s), 4754MiB/s-4754MiB/s (4985MB/s-4985MB/s), io=10.0GiB (10.7GB), run=2154-2154msec

```

New write speed:
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=16392: Thu May  4 03:24:41 2023
  write: IOPS=469, BW=470MiB/s (492MB/s)(10.0GiB/21806msec); 0 zone resets
    slat (usec): min=152, max=22963, avg=1511.83, stdev=755.32
    clat (usec): min=2, max=6320.1k, avg=65723.61, stdev=343811.00
     lat (usec): min=285, max=6322.6k, avg=67236.44, stdev=343884.22
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    9], 10.00th=[    9], 20.00th=[   13],
     | 30.00th=[   47], 40.00th=[   56], 50.00th=[   59], 60.00th=[   61],
     | 70.00th=[   62], 80.00th=[   63], 90.00th=[   64], 95.00th=[   65],
     | 99.00th=[   71], 99.50th=[   81], 99.90th=[ 6275], 99.95th=[ 6342],
     | 99.99th=[ 6342]
   bw (  KiB/s): min=483328, max=2957312, per=100.00%, avg=657835.90, stdev=494532.48, samples=31
   iops        : min=  472, max= 2888, avg=642.39, stdev=482.95, samples=31
  lat (usec)   : 4=0.03%, 10=0.01%, 20=0.01%, 500=0.03%, 750=0.02%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.12%, 4=0.20%, 10=15.82%, 20=7.46%, 50=7.78%
  lat (msec)   : 100=68.20%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=614, max=614, avg=614.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  612],  5.00th=[  612], 10.00th=[  612], 20.00th=[  612],
     | 30.00th=[  612], 40.00th=[  612], 50.00th=[  612], 60.00th=[  612],
     | 70.00th=[  612], 80.00th=[  612], 90.00th=[  612], 95.00th=[  612],
     | 99.00th=[  612], 99.50th=[  612], 99.90th=[  612], 99.95th=[  612],
     | 99.99th=[  612]
  cpu          : usr=2.28%, sys=15.49%, ctx=87622, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=470MiB/s (492MB/s), 470MiB/s-470MiB/s (492MB/s-492MB/s), io=10.0GiB (10.7GB), run=21806-21806msec

```

That's a lot better than it was, but I confess I wasn't able to get the disk IDs working in your code:  So I used Cockpit's ZFS GUI which omitted a few specifications.

The ashift value is now 9, I may attempt to increase that tomorrow.

For now, the pool is working and "fast enough".  Transferring my movie files ranged from 450BM/s to 490MB/s after the drive caches were full.

---

### Post by MAFoElffen on 2023-05-04
ashift is where a big part of the problem is... and what should have gave you better performance... That is in the zpool create command:
```

sudo zpool create \
    **[COLOR=#ff0000]-o ashift=12[/COLOR]** \
    -o autotrim=on \
    -O acltype=posixacl \
    -O xattr=sa \
    -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off \
    -O mountpoint=/Pool \
    Pool1 raidz3 \
    /dev/disk/by-id/disk1-part1 \
    /dev/disk/by-id/disk2-part1 \
    /dev/disk/by-id/disk3-part1 \
    /dev/disk/by-id/disk4-part1 \
    /dev/disk/by-id/disk5-part1 \
    /dev/disk/by-id/disk6-part1 \
    /dev/disk/by-id/disk7-part1 \
    /dev/disk/by-id/disk8-part1 \
    /dev/disk/by-id/disk9-part1

```
And that is the one property that cannot be changed without destroying the pool and then creating new, with the new setting. The is the one reason you had to start over. Curious how that did not change...

If you set that to ashift=12, then the default recordsize will be at 128K without having to declare it explicitly (otherwise you would have to add recordsize=128K to that create command).

Please redo that and test again.

---

### Post by MAFoElffen on 2023-05-04
On getting and using uniquely specific disk ID's, I use this command:
```

ls -l /dev/disk/by-id/ | grep -v 'loop'

```
This is going to give you output similar to this snippet from mine:
```

lrwxrwxrwx 1 root root  9 Apr 30 20:59 wwn-0x5000c500e4f159de -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 30 20:59 [COLOR=#ff0000]wwn-0x5000c500e4f159de-part1[/COLOR] -> ../../sda1

```
So that /dev/disk/by-id/wwn-0x5000c500e4f159de-part1 is what I use for /dev/sda1...

Mine is server / console. ssh in from a GUI desktop, from a graphical terminal. Have an editor open. Copy and paste the zpool create command into an editor. Run the list command above. copy and paste the diis-by-id names into the code, over the place-holders. When it all lots good, and acceptable, then copy and paste it into the terminal.

I'm lazy. I don't have to type everything from scratch into a live command prompt. I caan do it, but why? LOL Work smartly...

---

### Post by papriak on 2023-05-04
> **MAFoElffen said:**
> Please redo that and test again.

Like yesterday, I keep getting the error ```
"Cannot resolve path (Whatever I put for the first disk)"
```

I'm getting it with and without specifying the first partition.

I've tried replacing the disk number with the serial numbers and worldwide IDs, and they aren't working.  :(

---

### Post by MAFoElffen on 2023-05-04
Here is my terminal log today with the new pool def and it's tests:
```

mafoelffen@Mikes-B460M:~$ sudo zpool create \
    -o ashift=13 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off \
    -O mountpoint=/KVM_Pool \
    kpool raidz2 \
    /dev/disk/by-id/nvme-eui.0025385a2140bd61-part1 \
    /dev/disk/by-id/nvme-eui.0025385a21418769-part1 \
    /dev/disk/by-id/nvme-eui.0025385a2141f4fc-part1 \
    /dev/disk/by-id/nvme-eui.0025385b21407ef0-part1
mafoelffen@Mikes-B460M:~$ sudo zpool status -v kpool
  pool: kpool
 state: ONLINE
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ sudo zpool list kpool
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
kpool  7.27T  2.25M  7.27T        -         -     0%     0%  1.00x    ONLINE  -
mafoelffen@Mikes-B460M:~$ zfs create -o canmount=off -o mountpoint=none kpool/KVM
cannot create 'kpool/KVM': permission denied
mafoelffen@Mikes-B460M:~$ sudo zfs create -o canmount=off -o mountpoint=none kpool/KVM
mafoelffen@Mikes-B460M:~$ zfs create -o recordsize=4K -o mountpoint=/KVM_Pool kpool/KVM/ubuntu_2cwpns
cannot create 'kpool/KVM/ubuntu_2cwpns': permission denied
mafoelffen@Mikes-B460M:~$ sudo zfs create -o recordsize=4K -o mountpoint=/KVM_Pool kpool/KVM/ubuntu_2cwpns
mafoelffen@Mikes-B460M:~$ sudo chown -R mafoelffen:mafoelffen /KVM_Pool
mafoelffen@Mikes-B460M:~$ cd /KVM_Pool
mafoelffen@Mikes-B460M:/KVM_Pool$ for i in sync recordsize compression compressratio atime xattr logbias dedup acltype copies volblocksize; do sudo zfs get $i kpool/KVM/ubuntu_2cwpns; done | grep -v NAME
kpool/KVM/ubuntu_2cwpns  sync      standard  default
kpool/KVM/ubuntu_2cwpns  recordsize  4K       local
kpool/KVM/ubuntu_2cwpns  compression  lz4             inherited from kpool
kpool/KVM/ubuntu_2cwpns  compressratio  1.00x  -
kpool/KVM/ubuntu_2cwpns  atime     on     default
kpool/KVM/ubuntu_2cwpns  xattr     sa     inherited from kpool
kpool/KVM/ubuntu_2cwpns  logbias   latency     default
kpool/KVM/ubuntu_2cwpns  dedup     off            default
kpool/KVM/ubuntu_2cwpns  acltype   posix     inherited from kpool
kpool/KVM/ubuntu_2cwpns  copies    1       default
kpool/KVM/ubuntu_2cwpns  volblocksize  -         -
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool get ashift,feature@async_destroy,feature@empty_bpobj,feature@lz4_compress kpool
NAME   PROPERTY               VALUE                  SOURCE
kpool  ashift                 13                     local
kpool  feature@async_destroy  enabled                local
kpool  feature@empty_bpobj    active                 local
kpool  feature@lz4_compress   active                 local
mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [R(1)][100.0%][r=1565MiB/s][r=1565 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=145332: Thu May  4 14:13:04 2023
  read: IOPS=1550, BW=1550MiB/s (1626MB/s)(10.0GiB/6605msec)
    slat (usec): min=559, max=3736, avg=644.03, stdev=136.65
    clat (nsec): min=1214, max=86278k, avg=19769123.74, stdev=3479796.80
     lat (usec): min=578, max=88043, avg=20413.32, stdev=3574.13
    clat percentiles (usec):
     |  1.00th=[12780],  5.00th=[19268], 10.00th=[19530], 20.00th=[19530],
     | 30.00th=[19530], 40.00th=[19530], 50.00th=[19792], 60.00th=[19792],
     | 70.00th=[19792], 80.00th=[19792], 90.00th=[20055], 95.00th=[20055],
     | 99.00th=[21365], 99.50th=[25035], 99.90th=[83362], 99.95th=[85459],
     | 99.99th=[86508]
   bw (  MiB/s): min= 1258, max= 1596, per=99.71%, avg=1545.85, stdev=87.19, samples=13
   iops        : min= 1258, max= 1596, avg=1545.85, stdev=87.19, samples=13
  lat (usec)   : 2=0.05%, 750=0.05%
  lat (msec)   : 2=0.10%, 4=0.15%, 10=0.45%, 20=92.04%, 50=6.88%
  lat (msec)   : 100=0.29%
  cpu          : usr=0.29%, sys=99.68%, ctx=9, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1550MiB/s (1626MB/s), 1550MiB/s-1550MiB/s (1626MB/s-1626MB/s), io=10.0GiB (10.7GB), run=6605-6605msec
mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=720MiB/s][w=720 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][92.9%][w=657MiB/s][w=657 IOPS][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=602MiB/s][w=601 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=145483: Thu May  4 14:13:43 2023
  write: IOPS=701, BW=702MiB/s (736MB/s)(10.0GiB/14588msec); 0 zone resets
    slat (usec): min=893, max=4774, avg=1397.77, stdev=524.55
    clat (nsec): min=1328, max=296007k, avg=43832521.54, stdev=20568381.82
     lat (usec): min=935, max=298078, avg=45230.92, stdev=20949.22
    clat percentiles (msec):
     |  1.00th=[   27],  5.00th=[   30], 10.00th=[   30], 20.00th=[   30],
     | 30.00th=[   30], 40.00th=[   30], 50.00th=[   31], 60.00th=[   49],
     | 70.00th=[   61], 80.00th=[   63], 90.00th=[   64], 95.00th=[   66],
     | 99.00th=[   67], 99.50th=[   67], 99.90th=[  288], 99.95th=[  292],
     | 99.99th=[  296]
   bw (  KiB/s): min=382976, max=1011712, per=99.73%, avg=716863.59, stdev=188530.05, samples=29
   iops        : min=  374, max=  988, avg=700.03, stdev=184.11, samples=29
  lat (usec)   : 2=0.02%, 4=0.01%, 10=0.02%, 1000=0.02%
  lat (msec)   : 2=0.03%, 4=0.08%, 10=0.23%, 20=0.36%, 50=59.70%
  lat (msec)   : 100=39.23%, 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=2362, max=2362, avg=2362.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 2352],  5.00th=[ 2352], 10.00th=[ 2352], 20.00th=[ 2352],
     | 30.00th=[ 2352], 40.00th=[ 2352], 50.00th=[ 2352], 60.00th=[ 2352],
     | 70.00th=[ 2352], 80.00th=[ 2352], 90.00th=[ 2352], 95.00th=[ 2352],
     | 99.00th=[ 2352], 99.50th=[ 2352], 99.90th=[ 2352], 99.95th=[ 2352],
     | 99.99th=[ 2352]
  cpu          : usr=2.99%, sys=96.79%, ctx=356, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=702MiB/s (736MB/s), 702MiB/s-702MiB/s (736MB/s-736MB/s), io=10.0GiB (10.7GB), run=14588-14588msec
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0
    logs    
      nvme-PCIe_SSD_23011650000183-part1     ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000181-part1     ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool remove datapool nvme-PCIe_SSD_23011650000183-part1
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool remove datapool nvme-PCIe_SSD_23011650000181-part1
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool add kpool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part1
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool add -f kpool log /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part1
mafoelffen@Mikes-B460M:/KVM_Pool$ sudo zpool status -v kpool
  pool: kpool
 state: ONLINE
config:

    NAME                                  STATE     READ WRITE CKSUM
    kpool                                 ONLINE       0     0     0
      raidz2-0                            ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1   ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1   ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1   ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1   ONLINE       0     0     0
    logs    
      nvme-PCIe_SSD_23011650000183-part1  ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000181-part1  ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=1562MiB/s][r=1562 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=243793: Thu May  4 14:18:16 2023
  read: IOPS=1551, BW=1551MiB/s (1626MB/s)(10.0GiB/6602msec)
    slat (usec): min=543, max=5952, avg=643.55, stdev=202.17
    clat (nsec): min=1079, max=26025k, avg=19815197.12, stdev=1867540.81
     lat (usec): min=576, max=27735, avg=20458.94, stdev=1884.32
    clat percentiles (usec):
     |  1.00th=[12649],  5.00th=[19268], 10.00th=[19268], 20.00th=[19530],
     | 30.00th=[19530], 40.00th=[19530], 50.00th=[19792], 60.00th=[19792],
     | 70.00th=[19792], 80.00th=[20055], 90.00th=[20317], 95.00th=[22938],
     | 99.00th=[25297], 99.50th=[25297], 99.90th=[25822], 99.95th=[25822],
     | 99.99th=[25822]
   bw (  MiB/s): min= 1498, max= 1582, per=99.72%, avg=1546.77, stdev=24.13, samples=13
   iops        : min= 1498, max= 1582, avg=1546.77, stdev=24.13, samples=13
  lat (usec)   : 2=0.05%, 750=0.05%
  lat (msec)   : 2=0.10%, 4=0.14%, 10=0.45%, 20=82.61%, 50=16.61%
  cpu          : usr=0.11%, sys=99.85%, ctx=13, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1551MiB/s (1626MB/s), 1551MiB/s-1551MiB/s (1626MB/s-1626MB/s), io=10.0GiB (10.7GB), run=6602-6602msec
mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=765MiB/s][w=765 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][86.7%][w=686MiB/s][w=686 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=702MiB/s][w=701 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=243889: Thu May  4 14:18:55 2023
  write: IOPS=701, BW=702MiB/s (736MB/s)(10.0GiB/14595msec); 0 zone resets
    slat (usec): min=883, max=11371, avg=1417.01, stdev=508.57
    clat (nsec): min=1077, max=95264k, avg=43926345.15, stdev=13703834.11
     lat (usec): min=941, max=96770, avg=45343.95, stdev=14093.80
    clat percentiles (usec):
     |  1.00th=[22414],  5.00th=[29492], 10.00th=[29492], 20.00th=[29754],
     | 30.00th=[30016], 40.00th=[36963], 50.00th=[44303], 60.00th=[46924],
     | 70.00th=[53216], 80.00th=[59507], 90.00th=[62653], 95.00th=[64750],
     | 99.00th=[66323], 99.50th=[68682], 99.90th=[90702], 99.95th=[94897],
     | 99.99th=[94897]
   bw (  KiB/s): min=499712, max=1042432, per=99.72%, avg=716452.93, stdev=171778.17, samples=29
   iops        : min=  488, max= 1018, avg=699.62, stdev=167.77, samples=29
  lat (usec)   : 2=0.05%, 1000=0.05%
  lat (msec)   : 2=0.05%, 4=0.09%, 10=0.25%, 20=0.41%, 50=65.05%
  lat (msec)   : 100=34.05%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=534, max=534, avg=534.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  532],  5.00th=[  532], 10.00th=[  532], 20.00th=[  532],
     | 30.00th=[  532], 40.00th=[  532], 50.00th=[  532], 60.00th=[  532],
     | 70.00th=[  532], 80.00th=[  532], 90.00th=[  532], 95.00th=[  532],
     | 99.00th=[  532], 99.50th=[  532], 99.90th=[  532], 99.95th=[  532],
     | 99.99th=[  532]
  cpu          : usr=2.46%, sys=97.26%, ctx=291, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=702MiB/s (736MB/s), 702MiB/s-702MiB/s (736MB/s-736MB/s), io=10.0GiB (10.7GB), run=14595-14595msec

```
Take in mind that these drives spec are: Read Speed: Up to 3,500 MB/s · Sequential Write Speed: Up to 3,300 MB/s.

---

### Post by MAFoElffen on 2023-05-04
LMAO... 

By my stats on those tests, I see no difference on mine (at all) when I added SLOG and L2ARC to that pool, so I am going to remove them and add them back to the other pool which needs the caches for the vdev using HDD drives.

---

### Post by #&amp;thj^% on 2023-05-04
> **papriak said:**
> Like yesterday, I keep getting the error ```
"Cannot resolve path (Whatever I put for the first disk)"
```

I'm getting it with and without specifying the first partition.

I've tried replacing the disk number with the serial numbers and worldwide IDs, and they aren't working.  :(

I ran into that 2 months ago, look at :
```
systemctl status zfs-import-cache.service
&#9679; zfs-import-cache.service - Import ZFS pools by cache file
     Loaded: loaded (/usr/lib/systemd/system/zfs-import-cache.service; enabled;>
     Active: active (exited) since Thu 2023-05-04 16:26:41 MDT; 3s ago
       Docs: man:zpool(8)
    Process: 282606 ExecStart=/usr/bin/zpool import -c /etc/zfs/zpool.cache -aN>
   Main PID: 282606 (code=exited, status=0/SUCCESS)
        CPU: 13ms

```
And:
```
systemctl status zfs-mount.service
&#9679; zfs-mount.service - Mount ZFS filesystems
     Loaded: loaded (/usr/lib/systemd/system/zfs-mount.service; enabled; preset>
     Active: active (exited) since Thu 2023-05-04 16:28:15 MDT; 3s ago
       Docs: man:zfs(8)
    Process: 286789 ExecStart=/usr/bin/zfs mount -a (code=exited, status=0/SUCC>
   Main PID: 286789 (code=exited, status=0/SUCCESS)
        CPU: 18ms

```

---

### Post by papriak on 2023-05-04
Got it, thanks!

```
sudo zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl \
    -O xattr=sa \
    -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off \
    -O mountpoint=/Pool \
    Pool1 raidz3 \
    /dev/disk/by-id/scsi-35000cca249d18e47-part1 \
    /dev/disk/by-id/scsi-35000cca249d1d3e2-part1 \
    /dev/disk/by-id/scsi-35000cca249d2c49e-part1 \
    /dev/disk/by-id/scsi-35000cca24ce9c080-part1 \
    /dev/disk/by-id/scsi-35000cca24cee021f-part1 \
    /dev/disk/by-id/scsi-35000cca24ceec499-part1 \
    /dev/disk/by-id/scsi-35000cca24cf3fa7a-part1 \
    /dev/disk/by-id/scsi-35000cca24cf51b3f-part1
```

I'm now getting between 600MB/s and 750MB/s transferring from Windows to the pool.  :D


Edit:  Somehow FIO keeps testing my NVME drive, I seem to be unable to make it test the pool now, despite changing my directory to a folder within the pool.

---

### Post by #&amp;thj^% on 2023-05-04
> **papriak said:**
> 
I'm now getting between 600MB/s and 750MB/s transferring from Windows to the pool.  :D
Can I quote you>>>"Life's to short to run a slow computer"
Feeling pretty good about now aren't ya....:lolflag:

---

### Post by MAFoElffen on 2023-05-04
That is great!!!

Glad we found what was slowing that down.

So that part is solved now? LOL

Now I would add in that dedicated SLOG cache, and test again...

---

### Post by papriak on 2023-05-04
> **1fallen said:**
> Can I quote you>>>"Life's to short to run a slow computer"
Feeling pretty good about now aren't ya....:lolflag:

Yes you may, and yes I am.  :P

---

### Post by MAFoElffen on 2023-05-04
Tuned my new pool a bit. After removing the L2ARC and SLOG (and moving those back to my old datapool where is was really needed), and tweaking the recordsize value:
```

Run status group 0 (all jobs):
   READ: bw=5753MiB/s (6032MB/s), 5753MiB/s-5753MiB/s (6032MB/s-6032MB/s), io=10.0GiB (10.7GB), run=1780-1780msec
Run status group 0 (all jobs):
  WRITE: bw=2434MiB/s (2552MB/s), 2434MiB/s-2434MiB/s (2552MB/s-2552MB/s), io=10.0GiB (10.7GB), run=4207-4207msec

```
Curious to see yours after you add in the SLOG cache...

---

### Post by papriak on 2023-05-04
I want to benchmark the new pool, but somehow FIO keeps testing my NVMe drive.  I'm changing the terminal's directory to a folder within the pool first, but FIO keeps testing the NVMe.

What am I doing wrong?

---

### Post by MAFoElffen on 2023-05-05
I'm not sure. I change directory to a directory within the pool I want to test, then execute the commands.

The fio test that we are running creates a file named 'temp.file' in the current directory, and that is where it is testing. I remove the file each time so that the tests are consistent, and that I am sure it verifies where I am testing.
```

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][100.0%][w=2495MiB/s][w=2495 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1655010: Fri May  5 02:16:39 2023
  write: IOPS=2435, BW=2436MiB/s (2554MB/s)(10.0GiB/4204msec); 0 zone resets
    slat (usec): min=102, max=2941, avg=393.82, stdev=198.56
    clat (nsec): min=1426, max=148923k, avg=12632561.66, stdev=9028030.59
     lat (usec): min=148, max=149073, avg=13026.97, stdev=9106.13
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    7],
     | 30.00th=[    9], 40.00th=[   12], 50.00th=[   13], 60.00th=[   15],
     | 70.00th=[   17], 80.00th=[   18], 90.00th=[   18], 95.00th=[   20],
     | 99.00th=[   25], 99.50th=[   28], 99.90th=[  148], 99.95th=[  148],
     | 99.99th=[  150]
   bw (  MiB/s): min= 2206, max= 3234, per=100.00%, avg=2485.53, stdev=325.78, samples=8
   iops        : min= 2206, max= 3234, avg=2485.38, stdev=325.81, samples=8
  lat (usec)   : 2=0.01%, 4=0.02%, 10=0.02%, 250=0.01%, 500=0.04%
  lat (usec)   : 750=0.03%, 1000=0.03%
  lat (msec)   : 2=0.15%, 4=0.24%, 10=33.42%, 20=63.19%, 50=2.54%
  lat (msec)   : 250=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1006, max=1006, avg=1006.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1004],  5.00th=[ 1004], 10.00th=[ 1004], 20.00th=[ 1004],
     | 30.00th=[ 1004], 40.00th=[ 1004], 50.00th=[ 1004], 60.00th=[ 1004],
     | 70.00th=[ 1004], 80.00th=[ 1004], 90.00th=[ 1004], 95.00th=[ 1004],
     | 99.00th=[ 1004], 99.50th=[ 1004], 99.90th=[ 1004], 99.95th=[ 1004],
     | 99.99th=[ 1004]
  cpu          : usr=14.80%, sys=80.06%, ctx=1359, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2436MiB/s (2554MB/s), 2436MiB/s-2436MiB/s (2554MB/s-2554MB/s), io=10.0GiB (10.7GB), run=4204-4204msec
mafoelffen@Mikes-B460M:/KVM_Pool$ ls -l ./temp.file
-rw-r--r-- 1 mafoelffen mafoelffen 2147483648 May  5 02:16 ./temp.file
mafoelffen@Mikes-B460M:/KVM_Pool$ file ./temp.file
./temp.file: data
mafoelffen@Mikes-B460M:/KVM_Pool$ rm temp.file

```

---

### Post by papriak on 2023-05-05
> **MAFoElffen said:**
> I'm not sure. I change directory to a directory within the pool I want to test, then execute the commands.

Looks like the system just wanted to rest overnight, the commands worked today. XD

Read:
```
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=15312: Fri May  5 15:20:22 2023
  read: IOPS=4686, BW=4686MiB/s (4914MB/s)(10.0GiB/2185msec)
    slat (usec): min=192, max=696, avg=211.52, stdev=24.56
    clat (usec): min=2, max=18455, avg=6544.95, stdev=682.68
     lat (usec): min=203, max=19153, avg=6756.73, stdev=698.23
    clat percentiles (usec):
     |  1.00th=[ 4228],  5.00th=[ 6521], 10.00th=[ 6521], 20.00th=[ 6521],
     | 30.00th=[ 6521], 40.00th=[ 6521], 50.00th=[ 6521], 60.00th=[ 6521],
     | 70.00th=[ 6521], 80.00th=[ 6587], 90.00th=[ 6587], 95.00th=[ 6587],
     | 99.00th=[ 8586], 99.50th=[ 8586], 99.90th=[15270], 99.95th=[16909],
     | 99.99th=[18220]
   bw (  MiB/s): min= 4448, max= 4748, per=99.62%, avg=4668.50, stdev=147.24, samples=4
   iops        : min= 4448, max= 4748, avg=4668.50, stdev=147.24, samples=4
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.24%, 4=0.45%, 10=98.80%, 20=0.26%
  cpu          : usr=0.69%, sys=99.13%, ctx=10, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=4686MiB/s (4914MB/s), 4686MiB/s-4686MiB/s (4914MB/s-4914MB/s), io=10.0GiB (10.7GB), run=2185-2185msec

```


Write:
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=15398: Fri May  5 15:21:00 2023
  write: IOPS=432, BW=433MiB/s (454MB/s)(10.0GiB/23674msec); 0 zone resets
    slat (usec): min=130, max=15670, avg=1589.62, stdev=782.88
    clat (usec): min=2, max=7397.5k, avg=71358.02, stdev=403023.29
     lat (usec): min=187, max=7399.3k, avg=72948.51, stdev=403092.62
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    9], 10.00th=[   11], 20.00th=[   12],
     | 30.00th=[   47], 40.00th=[   57], 50.00th=[   62], 60.00th=[   64],
     | 70.00th=[   66], 80.00th=[   67], 90.00th=[   69], 95.00th=[   69],
     | 99.00th=[   71], 99.50th=[   81], 99.90th=[ 7349], 99.95th=[ 7416],
     | 99.99th=[ 7416]
   bw (  KiB/s): min=321536, max=2707456, per=100.00%, avg=618590.73, stdev=465062.76, samples=33
   iops        : min=  314, max= 2644, avg=604.09, stdev=454.16, samples=33
  lat (usec)   : 4=0.03%, 10=0.02%, 250=0.01%, 500=0.02%, 750=0.02%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.09%, 4=0.19%, 10=8.12%, 20=14.63%, 50=9.34%
  lat (msec)   : 100=67.23%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=613, max=613, avg=613.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  612],  5.00th=[  612], 10.00th=[  612], 20.00th=[  612],
     | 30.00th=[  612], 40.00th=[  612], 50.00th=[  612], 60.00th=[  612],
     | 70.00th=[  612], 80.00th=[  612], 90.00th=[  612], 95.00th=[  612],
     | 99.00th=[  612], 99.50th=[  612], 99.90th=[  612], 99.95th=[  612],
     | 99.99th=[  612]
  cpu          : usr=1.80%, sys=14.07%, ctx=71319, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=433MiB/s (454MB/s), 433MiB/s-433MiB/s (454MB/s-454MB/s), io=10.0GiB (10.7GB), run=23674-23674msec

```

---

### Post by MAFoElffen on 2023-05-05
Sorry for this post... LOL. 1fallen wanted to see pictures of my Ceacent PCiex16 NVM Express 4 drive On-board Bifurcation Card...

 Attached Pic's

Between the PCIe 3 cards, that is 6 NVMe drives- My kpool... Then the L2ARC & SLOG devices for datapool.

The 7th NVMe drive is on the motherboard. Then an SSD and HDD drives. All in that Mini ATX case.

---

### Post by papriak on 2023-05-05
> **MAFoElffen said:**
> Sorry for this post... LOL. 1fallen wanted to see pictures of my Ceacent PCiex16 NVM Express 4 drive On-board Bifurcation Card...

 Attached Pic's

Between the 3 cards, that is 6 NVMe drives- My kpool... Then the L2ARC & SLOG for datapool.

The 7th NVMe drive is on the motherboard. Then an SSD and HDD drives. All in that Mini ATX case.

*"Ludicrous speed!!!"*

I used to have one of those quad-NVMe cards, I put my game partition on it in RAID-0 and got about 13GB/s, but it didn't speed up the loading times like I hoped:  I presume they were going over the internet for anti-cheat checks.

---

### Post by MAFoElffen on 2023-05-05
So now that you have benchmarked it, you can add your cache(s) in?

---

### Post by papriak on 2023-05-05
> **MAFoElffen said:**
> So now that you have benchmarked it, you can add your cache(s) in?

That's my plan for tonight/this weekend, then I'll benchmark it again.  :)

---

### Post by #&amp;thj^% on 2023-05-05
> **MAFoElffen said:**
> Sorry for this post... LOL. 1fallen wanted to see pictures of my Ceacent PCiex16 NVM Express 4 drive On-board Bifurcation Card...

 Attached Pic's

Between the PCIe 3 cards, that is 6 NVMe drives- My kpool... Then the L2ARC & SLOG devices for datapool.

The 7th NVMe drive is on the motherboard. Then an SSD and HDD drives. All in that Mini ATX case.

Thank You MAFoElffen I can rest easy now, i ordered the right one..whoosh.;)

---

### Post by papriak on 2023-05-05
> **MAFoElffen said:**
> So now that you have benchmarked it, you can add your cache(s) in?

Just so I'm clear, what capacities do you advise for the L2ARC and SLOG SSDs?

---

### Post by MAFoElffen on 2023-05-06
SLOG is 16 to 64GB.

L2ARC should not be over 10 times the system RAM...

So for yours, a 320GB partition for your L2ARC. your could have 2 mirrored partitions of 64GB each to have a mirrored SLOG. All that would fit on a 500GB SSD.

Examples... When I add mine in:
```

mafoelffen@Mikes-B460M:~$ sudo zpool add kpool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part3
mafoelffen@Mikes-B460M:~$ sudo zpool add datapool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part3
mafoelffen@Mikes-B460M:~$ sudo zpool add -f kpool log mirror /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part1 /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part2
mafoelffen@Mikes-B460M:~$ sudo zpool add -f datapool log mirror /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part1 /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part2

```
And results in:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v
[sudo] password for mafoelffen: 
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Apr  9 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0
    logs    
      mirror-3                               ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000183-part1   ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000183-part2   ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000183-part3     ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
config:

    NAME                                    STATE     READ WRITE CKSUM
    kpool                                   ONLINE       0     0     0
      raidz2-0                              ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1     ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1     ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1     ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1     ONLINE       0     0     0
    logs    
      mirror-1                              ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part1  ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part2  ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000181-part3    ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:12 with 0 errors on Tue Apr 18 12:14:25 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
**************************************
But that is going off of what is published as recommended... Please wait a day or so. I'm testing and tweaking and getting different results. Even though is says only 16GB to 64 GB for SLOG... If I allocate more, it goes faster.

I have to go to work, then will test more when I get back home...

EDIT:
Yes. The documentation **LIES**. The recommendations there are wrong. As per my tests, the more space I allocated for SLOG, the faster the HDD driven pool tested. My max test was as 500GB, the size of that SSD I had.

---

### Post by MAFoElffen on 2023-05-06
*** ----> My test results showed such a dramatic change and difference... That I just ordered 2 more 2TB NVMe drives so I can see for myself where SLOG allocation starts falling off in performance... And seeing just how fast I can get mine.

---

### Post by #&amp;thj^% on 2023-05-06
I'll have to make a Citizen arrest for that kind of speed there Sir...[-X

---

### Post by papriak on 2023-05-06
> **MAFoElffen said:**
> SLOG is 16 to 64GB.

L2ARC should not be over 10 times the system RAM...

So for yours, a 320GB partition for your L2ARC. your could have 2 mirrored partitions of 64GB each to have a mirrored SLOG. All that would fit on a 500GB SSD.

Examples... When I add mine in:
```

mafoelffen@Mikes-B460M:~$ sudo zpool add kpool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part3
mafoelffen@Mikes-B460M:~$ sudo zpool add datapool cache /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part3
mafoelffen@Mikes-B460M:~$ sudo zpool add -f kpool log mirror /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part1 /dev/disk/by-id/nvme-PCIe_SSD_23011650000181-part2
mafoelffen@Mikes-B460M:~$ sudo zpool add -f datapool log mirror /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part1 /dev/disk/by-id/nvme-PCIe_SSD_23011650000183-part2

```
And results in:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v
[sudo] password for mafoelffen: 
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Apr  9 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0
    logs    
      mirror-3                               ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000183-part1   ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000183-part2   ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000183-part3     ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
config:

    NAME                                    STATE     READ WRITE CKSUM
    kpool                                   ONLINE       0     0     0
      raidz2-0                              ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1     ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1     ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1     ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1     ONLINE       0     0     0
    logs    
      mirror-1                              ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part1  ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part2  ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000181-part3    ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:12 with 0 errors on Tue Apr 18 12:14:25 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
**************************************
But that is going off of what is published as recommended... Please wait a day or so. I'm testing and tweaking and getting different results. Even though is says only 16GB to 64 GB for SLOG... If I allocate more, it goes faster.

I have to go to work, then will test more when I get back home...

EDIT:
Yes. The documentation **LIES**. The recommendations there are wrong. As per my tests, the more space I allocated for SLOG, the faster the HDD driven pool tested. My max test was as 500GB, the size of that SSD I had.

I bought two 500GB Samsung 870 EVOs locally, I'll partition one for 320GB of L2ARC as you specified.

I'm  curious about SLOG speed too, so I'll re-purpose my 2TB NVMe "Transfer"  SSD and let you know.  (I assume I can switch it back later if needed)

---

### Post by MAFoElffen on 2023-05-06
Yes... Lately I treat storage like a scratchpad. I just keep re-using it for other things. LOL

Quick to add and remove... The command to remove is
```

sudo zpool remove /dev/disk/by-id/[disk_name]

```

---

### Post by papriak on 2023-05-07
Here are the results of a 2TB PCIe3 NVMe cache drive with both sata3 SSDs mirrored for logs:


```
server@server:~$ sudo zpool status
  pool: Pool
 state: ONLINE
config:

        NAME                                                     STATE     READ WRITE CKSUM
        Pool                                                     ONLINE       0     0     0
          raidz3-0                                               ONLINE       0     0     0
            scsi-35000cca249d18e47-part1                         ONLINE       0     0     0
            scsi-35000cca249d1d3e2-part1                         ONLINE       0     0     0
            scsi-35000cca249d2c49e-part1                         ONLINE       0     0     0
            scsi-35000cca24ce9c080-part1                         ONLINE       0     0     0
            scsi-35000cca24cee021f-part1                         ONLINE       0     0     0
            scsi-35000cca24ceec499-part1                         ONLINE       0     0     0
            scsi-35000cca24cf3fa7a-part1                         ONLINE       0     0     0
            scsi-35000cca24cf51b3f-part1                         ONLINE       0     0     0
        logs
          mirror-2                                               ONLINE       0     0     0
            ata-Samsung_SSD_870_EVO_500GB_S6PXNM0TB42123E-part1  ONLINE       0     0     0
            ata-Samsung_SSD_870_EVO_500GB_S6PXNMFW202525E-part1  ONLINE       0     0     0
        cache
          nvme-eui.0000000001000000e4d25c7263125201-part1        ONLINE       0     0     0

errors: No known data errors
```


Read:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=4790MiB/s][r=4790 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=2723: Sun May  7 04:53:30 2023
  read: IOPS=2076, BW=2077MiB/s (2178MB/s)(10.0GiB/4931msec)
    slat (usec): min=159, max=79373, avg=479.30, stdev=1690.54
    clat (usec): min=2, max=105529, avg=14561.74, stdev=17701.25
     lat (usec): min=202, max=131380, avg=15041.34, stdev=18257.58
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    7], 10.00th=[    7], 20.00th=[    7],
     | 30.00th=[    7], 40.00th=[    7], 50.00th=[    7], 60.00th=[    7],
     | 70.00th=[    7], 80.00th=[    8], 90.00th=[   45], 95.00th=[   50],
     | 99.00th=[   85], 99.50th=[   92], 99.90th=[  102], 99.95th=[  104],
     | 99.99th=[  106]
   bw (  MiB/s): min=  450, max= 4800, per=87.24%, avg=1811.78, stdev=1859.83, samples=9
   iops        : min=  450, max= 4800, avg=1811.78, stdev=1859.83, samples=9
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.06%
  lat (msec)   : 2=0.20%, 4=0.44%, 10=79.26%, 20=0.21%, 50=14.79%
  lat (msec)   : 100=4.70%, 250=0.16%
  cpu          : usr=0.30%, sys=47.89%, ctx=1194, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2077MiB/s (2178MB/s), 2077MiB/s-2077MiB/s (2178MB/s-2178MB/s), io=10.0GiB (10.7GB), run=4931-4931msec
```

Write:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=545MiB/s][w=545 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][86.7%][w=502MiB/s][w=501 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=7508: Sun May  7 04:54:40 2023
  write: IOPS=431, BW=431MiB/s (452MB/s)(10.0GiB/23741msec); 0 zone resets
    slat (usec): min=169, max=16743, avg=1578.26, stdev=793.26
    clat (usec): min=2, max=7572.0k, avg=71560.83, stdev=412705.35
     lat (usec): min=240, max=7573.7k, avg=73139.92, stdev=412759.74
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[    8], 10.00th=[    9], 20.00th=[   11],
     | 30.00th=[   47], 40.00th=[   57], 50.00th=[   62], 60.00th=[   64],
     | 70.00th=[   65], 80.00th=[   67], 90.00th=[   68], 95.00th=[   69],
     | 99.00th=[   73], 99.50th=[   78], 99.90th=[ 7550], 99.95th=[ 7550],
     | 99.99th=[ 7550]
   bw (  KiB/s): min=155208, max=3461120, per=100.00%, avg=618296.48, stdev=540561.42, samples=33
   iops        : min=  151, max= 3380, avg=603.79, stdev=527.91, samples=33
  lat (usec)   : 4=0.04%, 10=0.01%, 250=0.02%, 500=0.01%, 750=0.03%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.08%, 4=0.20%, 10=19.47%, 20=3.28%, 50=8.57%
  lat (msec)   : 100=67.97%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=681, max=681, avg=681.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  684],  5.00th=[  684], 10.00th=[  684], 20.00th=[  684],
     | 30.00th=[  684], 40.00th=[  684], 50.00th=[  684], 60.00th=[  684],
     | 70.00th=[  684], 80.00th=[  684], 90.00th=[  684], 95.00th=[  684],
     | 99.00th=[  684], 99.50th=[  684], 99.90th=[  684], 99.95th=[  684],
     | 99.99th=[  684]
  cpu          : usr=2.06%, sys=15.53%, ctx=70942, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=431MiB/s (452MB/s), 431MiB/s-431MiB/s (452MB/s-452MB/s), io=10.0GiB (10.7GB), run=23741-23741msec
```

It started transferring at 1GB/s, but slowed to 400MB/s for most of my "real world" network transfer test.  (Eighteen .mp4 files ranging from 1-3 gigabytes each)

---

### Post by MAFoElffen on 2023-05-07
The one that is the write cache, SLOG, shows up in the zpool status as "LOG". L2ARC is read cache, and shows up in the zpool status as "CACHE". 

You have them mounted reversed.

Please try your L2ARC read cache as 320GB with an SSD, and the SLOG write log cache as the 2TB NVMe (single instead of mirrored)... Then we could see how that goes(?)

---

### Post by MAFoElffen on 2023-05-07
Oh, yes... There is going to be a trick you need to use to remove a mirrored log cache.

If you try to use the command:
```

sudo zpool remove Pool /dev/disk/by-id/ata-Samsung_SSD_870_EVO_500GB_S6PXNM0TB42123E-part1 /dev/disk/by-id/ata-Samsung_SSD_870_EVO_500GB_S6PXNMFW202525E-part1

```
... because it is mirrored, it is going to throw an error saying you can't do that for this type of device, or words to that effect. That is because the drives are nested within the cache's mirror vdev. 

You have to tell it remove the mirror device itself. So the commands are going to be
```

sudo zpool remove Pool mirror-2
sudo zpool remove Pool /dev/disk/by-id/nvme-eui.0000000001000000e4d25c7263125201-part1

sudo zpool add Pool cache /dev/disk/by-id/ata-Samsung_SSD_870_EVO_500GB_S6PXNM0TB42123E-part1
sudo zpool add -f Pool log /dev/disk/by-id/nvme-eui.0000000001000000e4d25c7263125201-part1

```

---

### Post by papriak on 2023-05-07
> **MAFoElffen said:**
> You have them mounted reversed.

*Head-desks*

Okay, let's try it again.

```
server@server:~$ sudo zpool status
  pool: Pool
 state: ONLINE
config:

        NAME                                                   STATE     READ WRITE CKSUM
        Pool                                                   ONLINE       0     0     0
          raidz3-0                                             ONLINE       0     0     0
            scsi-35000cca249d18e47-part1                       ONLINE       0     0     0
            scsi-35000cca249d1d3e2-part1                       ONLINE       0     0     0
            scsi-35000cca249d2c49e-part1                       ONLINE       0     0     0
            scsi-35000cca24ce9c080-part1                       ONLINE       0     0     0
            scsi-35000cca24cee021f-part1                       ONLINE       0     0     0
            scsi-35000cca24ceec499-part1                       ONLINE       0     0     0
            scsi-35000cca24cf3fa7a-part1                       ONLINE       0     0     0
            scsi-35000cca24cf51b3f-part1                       ONLINE       0     0     0
        logs
          nvme-eui.0000000001000000e4d25c7263125201-part1      ONLINE       0     0     0
        cache
          ata-Samsung_SSD_870_EVO_500GB_S6PXNM0TB42123E-part1  ONLINE       0     0     0

errors: No known data errors
```


Read:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
[sudo] password for server: 
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][100.0%][r=4717MiB/s][r=4717 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=2652: Sun May  7 16:05:36 2023
  read: IOPS=2067, BW=2068MiB/s (2168MB/s)(10.0GiB/4952msec)
    slat (usec): min=150, max=97356, avg=481.07, stdev=1924.27
    clat (usec): min=2, max=140055, avg=14607.89, stdev=18193.64
     lat (usec): min=203, max=140434, avg=15089.30, stdev=18743.11
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    7], 10.00th=[    7], 20.00th=[    7],
     | 30.00th=[    7], 40.00th=[    7], 50.00th=[    7], 60.00th=[    7],
     | 70.00th=[    7], 80.00th=[    8], 90.00th=[   45], 95.00th=[   50],
     | 99.00th=[   83], 99.50th=[  101], 99.90th=[  132], 99.95th=[  136],
     | 99.99th=[  140]
   bw (  MiB/s): min=  468, max= 4716, per=86.87%, avg=1796.44, stdev=1826.17, samples=9
   iops        : min=  468, max= 4716, avg=1796.44, stdev=1826.17, samples=9
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.36%, 10=79.29%, 20=0.47%, 50=14.49%
  lat (msec)   : 100=4.48%, 250=0.47%
  cpu          : usr=0.14%, sys=48.50%, ctx=1289, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2068MiB/s (2168MB/s), 2068MiB/s-2068MiB/s (2168MB/s-2168MB/s), io=10.0GiB (10.7GB), run=4952-4952msec
```

Write:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=461MiB/s][w=461 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][81.2%][w=558MiB/s][w=558 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=7480: Sun May  7 16:07:15 2023
  write: IOPS=482, BW=483MiB/s (506MB/s)(10.0GiB/21211msec); 0 zone resets
    slat (usec): min=167, max=17581, avg=1587.21, stdev=786.32
    clat (usec): min=2, max=4958.1k, avg=63897.05, stdev=269401.26
     lat (usec): min=224, max=4959.8k, avg=65485.06, stdev=269486.01
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[    8], 10.00th=[    9], 20.00th=[   11],
     | 30.00th=[   47], 40.00th=[   57], 50.00th=[   62], 60.00th=[   64],
     | 70.00th=[   66], 80.00th=[   67], 90.00th=[   68], 95.00th=[   70],
     | 99.00th=[   72], 99.50th=[   81], 99.90th=[ 4933], 99.95th=[ 4933],
     | 99.99th=[ 4933]
   bw (  KiB/s): min=290816, max=3346432, per=100.00%, avg=618682.18, stdev=524476.56, samples=33
   iops        : min=  284, max= 3268, avg=604.18, stdev=512.18, samples=33
  lat (usec)   : 4=0.03%, 10=0.02%, 250=0.01%, 500=0.02%, 750=0.02%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.08%, 4=0.20%, 10=17.29%, 20=5.58%, 50=8.69%
  lat (msec)   : 100=67.75%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=961, max=961, avg=961.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  964],  5.00th=[  964], 10.00th=[  964], 20.00th=[  964],
     | 30.00th=[  964], 40.00th=[  964], 50.00th=[  964], 60.00th=[  964],
     | 70.00th=[  964], 80.00th=[  964], 90.00th=[  964], 95.00th=[  964],
     | 99.00th=[  964], 99.50th=[  964], 99.90th=[  964], 99.95th=[  964],
     | 99.99th=[  964]
  cpu          : usr=2.15%, sys=13.38%, ctx=67947, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=483MiB/s (506MB/s), 483MiB/s-483MiB/s (506MB/s-506MB/s), io=10.0GiB (10.7GB), run=21211-21211msec
```

Not much of a difference here, nor in my data transfer test...

---

### Post by #&amp;thj^% on 2023-05-07
> **papriak said:**
> 
Not much of a difference here, nor in my data transfer test...
I'm guessing the added Drives are Spinning Drive then right?

---

### Post by papriak on 2023-05-07
> **1fallen said:**
> I'm guessing the added Drives are Spinning Drive then right?

They're two brand new 500GB Samsung 870 EVO SSDs, and the 2TB drive is an Intel 660 NVMe if I remember right.

---

### Post by #&amp;thj^% on 2023-05-07
Are you content with the speed now?
I'm kind of shooting from the hip here, Ive ordered 4@ 2TB NVMe drives to see how hard i can push the write speed.
So far with 2only NVMe's I'm getting:
```
Run status group 0 (all jobs):
  WRITE: bw=1258MiB/s (1319MB/s), 1258MiB/s-1258MiB/s (1319MB/s-1319MB/s), io=10.0GiB (10.7GB), run=8141-8141msec
```

---

### Post by papriak on 2023-05-07
> **1fallen said:**
> Are you content with the speed now?
I'm kind of shooting from the hip here, Ive ordered 4@ 2TB NVMe drives to see how hard i can push the write speed.
So far with 2only NVMe's I'm getting:
```
Run status group 0 (all jobs):
  WRITE: bw=1258MiB/s (1319MB/s), 1258MiB/s-1258MiB/s (1319MB/s-1319MB/s), io=10.0GiB (10.7GB), run=8141-8141msec
```

Do you think it's possible for me to achieve 500 or even 600 megabytes per second after the spinning drive's caches are saturated?

I thought my 2TB NVMe drive was going to store cache overflow as it was written to the spinning drives?

---

### Post by #&amp;thj^% on 2023-05-07
I'm only guessing until the drives arrive on 15th, but it seems you should, and heaven forbid if I'm wrong.

---

### Post by MAFoElffen on 2023-05-07
I would think that the cache fills and is written there, until the HHD vdevs catch up with their writes. 

My drives get here this Wednesday, the 10th. (Though I do have my eyes on some 4TB NVMe's from there. LOL).

I would have expected the cache to wait until it reached 2TB (full), until it fell off.

I was thinking (which can be dangerous. LOL). Since your files are so big, and they are video files, I am wondering if you got a speed increase by resetting the dataset recordsize=1M?

---

### Post by #&amp;thj^% on 2023-05-07
> **MAFoElffen said:**
> 

I was thinking (which can be dangerous. LOL). Since your files are so big, and they are video files, I am wondering if you got a speed increase by resetting the dataset recordsize=1M?
+1 Again great minds think alike

---

### Post by MAFoElffen on 2023-05-07
> **papriak said:**
> Do you think it's possible for me to achieve 500 or even 600 megabytes per second after the spinning drive's caches are saturated?
You are at least PCIe generation 3.0 right?
```

PCI Express: Unidirectional Bandwidth in x1 and x16 Configurations

Generation     Year of Release     Data Transfer Rate     Bandwidth x1     Bandwidth x16
PCIe 1.0       2003                2.5 GT/s               250 MB/s         4.0 GB/s
PCIe 2.0       2007                5.0 GT/s               500 MB/s         8.0 GB/s
PCIe 3.0       2010                8.0 GT/s               1 GB/s           16 GB/s
PCIe 4.0       2017                16 GT/s                2 GB/s           32 GB/s
PCIe 5.0       2019                32 GT/s                4 GB/s           64 GB/s
PCIe 6.0       2021                64 GT/s                8 GB/s           128 GB/s

```

---

### Post by MAFoElffen on 2023-05-07
I just looked up the spec's of your ASUS Z97-A motherboard
```

2 x PCIe 3.0/2.0 x16 (x16 or dual x8) 
1 x PCIe 2.0 x16 (x2 mode) 
2 x PCIe 2.0 x1  *[SUP]1[/SUP]
2 x PCI

```
So I would guess that depends in which slot you put that HBA card into. There is only two PCIe slots that are Gen 3.0.

EDIT: But with the test results so far, I am optimistic.

---

### Post by papriak on 2023-05-07
[QUOTE=MAFoElffen;14142044]You are at least PCIe generation 3.0 right?

Good point...

(Swaps my HBA and NVMe Adapter card positions, the boot/Ubuntu SSD is now on the PCIe 2.0 slot)


Read:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
[sudo] password for server: 
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][46.7%][r=821MiB/s][r=821 IOPS][eta 00m:08s]
Jobs: 1 (f=1): [R(1)][90.0%][r=3836MiB/s][r=3836 IOPS][eta 00m:01s]
TEST: (groupid=0, jobs=1): err= 0: pid=246929: Sun May  7 22:04:29 2023
  read: IOPS=1121, BW=1121MiB/s (1176MB/s)(10.0GiB/9131msec)
    slat (usec): min=174, max=168205, avg=888.88, stdev=3213.92
    clat (usec): min=2, max=201731, avg=27064.46, stdev=25623.57
     lat (usec): min=205, max=202675, avg=27953.70, stdev=26300.39
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    7], 10.00th=[    7], 20.00th=[    7],
     | 30.00th=[    7], 40.00th=[    7], 50.00th=[   14], 60.00th=[   40],
     | 70.00th=[   42], 80.00th=[   44], 90.00th=[   54], 95.00th=[   71],
     | 99.00th=[  113], 99.50th=[  144], 99.90th=[  190], 99.95th=[  201],
     | 99.99th=[  203]
   bw (  MiB/s): min=  412, max= 4738, per=95.16%, avg=1067.22, stdev=1190.80, samples=18
   iops        : min=  412, max= 4738, avg=1067.22, stdev=1190.80, samples=18
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.24%, 4=0.47%, 10=47.58%, 20=4.19%, 50=35.75%
  lat (msec)   : 100=10.08%, 250=1.45%
  cpu          : usr=0.51%, sys=30.21%, ctx=5999, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1121MiB/s (1176MB/s), 1121MiB/s-1121MiB/s (1176MB/s-1176MB/s), io=10.0GiB (10.7GB), run=9131-9131msec
```


Write:
```
server@server:/Pool/Backups/Backups$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][58.3%][w=572MiB/s][w=572 IOPS][eta 00m:05s]
Jobs: 1 (f=1): [W(1)][86.7%][w=605MiB/s][w=605 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
TEST: (groupid=0, jobs=1): err= 0: pid=260190: Sun May  7 22:06:05 2023
  write: IOPS=548, BW=548MiB/s (575MB/s)(10.0GiB/18682msec); 0 zone resets
    slat (usec): min=167, max=29871, avg=1411.78, stdev=822.70
    clat (usec): min=2, max=4213.4k, avg=56293.01, stdev=228566.06
     lat (usec): min=233, max=4215.2k, avg=57705.71, stdev=228643.94
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    9], 20.00th=[   13],
     | 30.00th=[   45], 40.00th=[   51], 50.00th=[   54], 60.00th=[   56],
     | 70.00th=[   57], 80.00th=[   58], 90.00th=[   61], 95.00th=[   64],
     | 99.00th=[   79], 99.50th=[   86], 99.90th=[ 4212], 99.95th=[ 4212],
     | 99.99th=[ 4212]
   bw (  KiB/s): min=475136, max=2471936, per=100.00%, avg=702854.03, stdev=490123.59, samples=29
   iops        : min=  464, max= 2414, avg=686.31, stdev=478.63, samples=29
  lat (usec)   : 4=0.03%, 20=0.02%, 250=0.01%, 500=0.01%, 750=0.02%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.09%, 4=0.23%, 10=10.98%, 20=12.77%, 50=14.90%
  lat (msec)   : 100=60.62%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=656, max=656, avg=656.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  660],  5.00th=[  660], 10.00th=[  660], 20.00th=[  660],
     | 30.00th=[  660], 40.00th=[  660], 50.00th=[  660], 60.00th=[  660],
     | 70.00th=[  660], 80.00th=[  660], 90.00th=[  660], 95.00th=[  660],
     | 99.00th=[  660], 99.50th=[  660], 99.90th=[  660], 99.95th=[  660],
     | 99.99th=[  660]
  cpu          : usr=2.47%, sys=20.71%, ctx=71346, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=548MiB/s (575MB/s), 548MiB/s-548MiB/s (575MB/s-575MB/s), io=10.0GiB (10.7GB), run=18682-18682msec
```

I'm now getting 1GB/s transfer speeds at first, then it slows to roughly 500MB/s with minor fluctuations.

I can live with that transfer rate for the spinning disks, but is there a way to make the Intel SSD hold the transferred data until the spinners catch up?

---

### Post by MAFoElffen on 2023-05-07
(On break at work) I'll know more about that Wednesday when my NVMe drives get here so I can see for myself. Otherwise I'd be guessing on that.

We already brought it up from 10m/s to 1G burst // 500M/s sustained... LOL

---

### Post by papriak on 2023-05-07
> **MAFoElffen said:**
> (On break at work) I'll know more about that Wednesday when my NVMe drives get here so I can see for myself. Otherwise I'd be guessing on that.

We already brought it up from 10m/s to 1G burst // 500M/s sustained... LOL

Alright, I'll wait.


Thanks for continuing to assist me.  :)

---

### Post by MAFoElffen on 2023-05-08
Last night while at work, I was thinking that until the new drives came, that I would test in a Linux Server kind of way... LOL. Something to simulate asynchronous processing with multi-user, multi-thread, and multiple files as once. That is more realistic for a Linux Server filesystem right?

My CPU has 10 cores/20 threads... I tested with 18 threads/18 files of 10GB each, with 1MB recordsize at once:
```

mafoelffen@Mikes-B460M:~$ iozone -R -l 18 -u 18 -r 1m -s 10g -F /data/KVM-VM/f1 /data/KVM-VM/f2 /data/KVM-VM/f3 /data/KVM-VM/f4 /data/KVM-VM/f5 /data/KVM-VM/f6 /data/KVM-VM/f7 /data/KVM-VM/f8 /data/KVM-VM/f9 /data/KVM-VM/f10 /data/KVM-VM/f11 /data/KVM-VM/f12 /data/KVM-VM/f13 /data/KVM-VM/f14 /data/KVM-VM/f15 /data/KVM-VM/f16 /data/KVM-VM/f17 /data/KVM-VM/f18
    Iozone: Performance Test of File I/O
            Version $Revision: 3.489 $
        Compiled for 64 bit mode.
        Build: linux-AMD64 

    Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
                 Al Slater, Scott Rhine, Mike Wisner, Ken Goss
                 Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
                 Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
                 Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy, Dave Boone,
                 Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root,
                 Fabrice Bacchella, Zhenghua Xue, Qin Li, Darren Sawyer,
                 Vangel Bojaxhi, Ben England, Vikentsi Lapa,
                 Alexey Skidanov, Sudhir Kumar.

    Run began: Mon May  8 03:15:44 2023

    Excel chart generation enabled
    Record Size 1024 kB
    File size set to 10485760 kB
    Command line used: iozone -R -l 18 -u 18 -r 1m -s 10g -F /data/KVM-VM/f1 /data/KVM-VM/f2 /data/KVM-VM/f3 /data/KVM-VM/f4 /data/KVM-VM/f5 /data/KVM-VM/f6 /data/KVM-VM/f7 /data/KVM-VM/f8 /data/KVM-VM/f9 /data/KVM-VM/f10 /data/KVM-VM/f11 /data/KVM-VM/f12 /data/KVM-VM/f13 /data/KVM-VM/f14 /data/KVM-VM/f15 /data/KVM-VM/f16 /data/KVM-VM/f17 /data/KVM-VM/f18
    Output is in kBytes/sec
    Time Resolution = 0.000001 seconds.
    Processor cache size set to 1024 kBytes.
    Processor cache line size set to 32 bytes.
    File stride size set to 17 * record size.
    Min process = 18 
    Max process = 18 
    Throughput test with 18 processes
    Each process writes a 10485760 kByte file in 1024 kByte records

    Children see throughput for 18 initial writers     = 2819680.48 kB/sec
    Parent sees throughput for 18 initial writers     = 2553742.42 kB/sec
    Min throughput per process             =  153434.86 kB/sec 
    Max throughput per process             =  160128.97 kB/sec
    Avg throughput per process             =  156648.92 kB/sec
    Min xfer                     = 10048512.00 kB

    Children see throughput for 18 rewriters     = 2829550.33 kB/sec
    Parent sees throughput for 18 rewriters     = 2624574.62 kB/sec
    Min throughput per process             =  154151.28 kB/sec 
    Max throughput per process             =  164773.17 kB/sec
    Avg throughput per process             =  157197.24 kB/sec
    Min xfer                     = 9809920.00 kB

    Children see throughput for 18 readers         = 7566505.25 kB/sec
    Parent sees throughput for 18 readers         = 7566077.78 kB/sec
    Min throughput per process             =  362861.03 kB/sec 
    Max throughput per process             =  519927.91 kB/sec
    Avg throughput per process             =  420361.40 kB/sec
    Min xfer                     = 7318528.00 kB

    Children see throughput for 18 re-readers     = 7568120.84 kB/sec
    Parent sees throughput for 18 re-readers     = 7567618.45 kB/sec
    Min throughput per process             =  362659.41 kB/sec 
    Max throughput per process             =  550415.00 kB/sec
    Avg throughput per process             =  420451.16 kB/sec
    Min xfer                     = 6908928.00 kB

    Children see throughput for 18 reverse readers     = 7564575.69 kB/sec
    Parent sees throughput for 18 reverse readers     = 7564147.65 kB/sec
    Min throughput per process             =  362464.22 kB/sec 
    Max throughput per process             =  551546.44 kB/sec
    Avg throughput per process             =  420254.20 kB/sec
    Min xfer                     = 6891520.00 kB

    Children see throughput for 18 stride readers     = 7489778.50 kB/sec
    Parent sees throughput for 18 stride readers     = 7489203.32 kB/sec
    Min throughput per process             =  359094.69 kB/sec 
    Max throughput per process             =  659502.44 kB/sec
    Avg throughput per process             =  416098.81 kB/sec
    Min xfer                     = 5709824.00 kB

    Children see throughput for 18 random readers     = 7335490.75 kB/sec
    Parent sees throughput for 18 random readers     = 7334900.27 kB/sec
    Min throughput per process             =  351316.69 kB/sec 
    Max throughput per process             =  596998.25 kB/sec
    Avg throughput per process             =  407527.26 kB/sec
    Min xfer                     = 6170624.00 kB

    Children see throughput for 18 mixed workload     = 8556531.94 kB/sec
    Parent sees throughput for 18 mixed workload     = 2971456.41 kB/sec
    Min throughput per process             =  278769.50 kB/sec 
    Max throughput per process             =  730811.31 kB/sec
    Avg throughput per process             =  475362.89 kB/sec
    Min xfer                     = 4003840.00 kB

    Children see throughput for 18 random writers     = 2369023.09 kB/sec
    Parent sees throughput for 18 random writers     = 2103190.34 kB/sec
    Min throughput per process             =  128643.69 kB/sec 
    Max throughput per process             =  137820.61 kB/sec
    Avg throughput per process             =  131612.39 kB/sec
    Min xfer                     = 9788416.00 kB

    Children see throughput for 18 pwrite writers     = 2913170.81 kB/sec
    Parent sees throughput for 18 pwrite writers     = 2547725.39 kB/sec
    Min throughput per process             =  157164.86 kB/sec 
    Max throughput per process             =  169124.59 kB/sec
    Avg throughput per process             =  161842.82 kB/sec
    Min xfer                     = 9744384.00 kB

    Children see throughput for 18 pread readers     = 7548155.78 kB/sec
    Parent sees throughput for 18 pread readers     = 7547630.18 kB/sec
    Min throughput per process             =  362183.12 kB/sec 
    Max throughput per process             =  640612.75 kB/sec
    Avg throughput per process             =  419341.99 kB/sec
    Min xfer                     = 5928960.00 kB

    Children see throughput for 18 fwriters     = 3063177.88 kB/sec
    Parent sees throughput for 18 fwriters         = 2739172.49 kB/sec
    Min throughput per process             =  162933.69 kB/sec 
    Max throughput per process             =  177951.45 kB/sec
    Avg throughput per process             =  170176.55 kB/sec
    Min xfer                     = 10485760.00 kB

    Children see throughput for 18 freaders     = 8662451.22 kB/sec
    Parent sees throughput for 18 freaders         = 7931658.11 kB/sec
    Min throughput per process             =  440658.22 kB/sec 
    Max throughput per process             =  636420.06 kB/sec
    Avg throughput per process             =  481247.29 kB/sec
    Min xfer                     = 10485760.00 kB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 1024 kBytes "
"Output is in kBytes/sec"

"  Initial write " 2819680.48 

"        Rewrite " 2829550.33 

"           Read " 7566505.25 

"        Re-read " 7568120.84 

"   Reverse Read " 7564575.69 

"    Stride read " 7489778.50 

"    Random read " 7335490.75 

" Mixed workload " 8556531.94 

"   Random write " 2369023.09 

"         Pwrite " 2913170.81 

"          Pread " 7548155.78 

"         Fwrite " 3063177.88 

"          Fread " 8662451.22 


iozone test complete.
mafoelffen@Mikes-B460M:~$ iozone -R -l 18 -u 18 -r 1m -s 10g -F /KVM_Pool/KVM-VM/f1 /KVM_Pool/KVM-VM/f2 /KVM_Pool/KVM-VM/f3 /KVM_Pool/KVM-VM/f4 /KVM_Pool/KVM-VM/f5 /KVM_Pool/KVM-VM/f6 /KVM_Pool/KVM-VM/f7 /KVM_Pool/KVM-VM/f8 /KVM_Pool/KVM-VM/f9 /KVM_Pool/KVM-VM/f10 /KVM_Pool/KVM-VM/f11 /KVM_Pool/KVM-VM/f12 /KVM_Pool/KVM-VM/f13 /KVM_Pool/KVM-VM/f14 /KVM_Pool/KVM-VM/f15 /KVM_Pool/KVM-VM/f16 /KVM_Pool/KVM-VM/f17 /KVM_Pool/KVM-VM/f18
    Iozone: Performance Test of File I/O
            Version $Revision: 3.489 $
        Compiled for 64 bit mode.
        Build: linux-AMD64 

    Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
                 Al Slater, Scott Rhine, Mike Wisner, Ken Goss
                 Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
                 Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
                 Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy, Dave Boone,
                 Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root,
                 Fabrice Bacchella, Zhenghua Xue, Qin Li, Darren Sawyer,
                 Vangel Bojaxhi, Ben England, Vikentsi Lapa,
                 Alexey Skidanov, Sudhir Kumar.

    Run began: Mon May  8 03:35:23 2023

    Excel chart generation enabled
    Record Size 1024 kB
    File size set to 10485760 kB
    Command line used: iozone -R -l 18 -u 18 -r 1m -s 10g -F /KVM_Pool/KVM-VM/f1 /KVM_Pool/KVM-VM/f2 /KVM_Pool/KVM-VM/f3 /KVM_Pool/KVM-VM/f4 /KVM_Pool/KVM-VM/f5 /KVM_Pool/KVM-VM/f6 /KVM_Pool/KVM-VM/f7 /KVM_Pool/KVM-VM/f8 /KVM_Pool/KVM-VM/f9 /KVM_Pool/KVM-VM/f10 /KVM_Pool/KVM-VM/f11 /KVM_Pool/KVM-VM/f12 /KVM_Pool/KVM-VM/f13 /KVM_Pool/KVM-VM/f14 /KVM_Pool/KVM-VM/f15 /KVM_Pool/KVM-VM/f16 /KVM_Pool/KVM-VM/f17 /KVM_Pool/KVM-VM/f18
    Output is in kBytes/sec
    Time Resolution = 0.000001 seconds.
    Processor cache size set to 1024 kBytes.
    Processor cache line size set to 32 bytes.
    File stride size set to 17 * record size.
    Min process = 18 
    Max process = 18 
    Throughput test with 18 processes
    Each process writes a 10485760 kByte file in 1024 kByte records

    Children see throughput for 18 initial writers     = 8346941.12 kB/sec
    Parent sees throughput for 18 initial writers     = 5275552.56 kB/sec
    Min throughput per process             =  436762.69 kB/sec 
    Max throughput per process             =  482852.66 kB/sec
    Avg throughput per process             =  463718.95 kB/sec
    Min xfer                     = 9491456.00 kB

    Children see throughput for 18 rewriters     = 8077831.41 kB/sec
    Parent sees throughput for 18 rewriters     = 7177802.37 kB/sec
    Min throughput per process             =  415567.66 kB/sec 
    Max throughput per process             =  502485.53 kB/sec
    Avg throughput per process             =  448768.41 kB/sec
    Min xfer                     = 8672256.00 kB

    Children see throughput for 18 readers         = 7529366.47 kB/sec
    Parent sees throughput for 18 readers         = 7528931.44 kB/sec
    Min throughput per process             =  360497.09 kB/sec 
    Max throughput per process             =  511530.56 kB/sec
    Avg throughput per process             =  418298.14 kB/sec
    Min xfer                     = 7390208.00 kB

    Children see throughput for 18 re-readers     = 7524155.94 kB/sec
    Parent sees throughput for 18 re-readers     = 7523677.36 kB/sec
    Min throughput per process             =  362224.97 kB/sec 
    Max throughput per process             =  544689.38 kB/sec
    Avg throughput per process             =  418008.66 kB/sec
    Min xfer                     = 6973440.00 kB

    Children see throughput for 18 reverse readers     = 7555020.53 kB/sec
    Parent sees throughput for 18 reverse readers     = 7554589.43 kB/sec
    Min throughput per process             =  360327.50 kB/sec 
    Max throughput per process             =  498222.25 kB/sec
    Avg throughput per process             =  419723.36 kB/sec
    Min xfer                     = 7583744.00 kB

    Children see throughput for 18 stride readers     = 7473573.38 kB/sec
    Parent sees throughput for 18 stride readers     = 7473010.81 kB/sec
    Min throughput per process             =  356511.09 kB/sec 
    Max throughput per process             =  645260.75 kB/sec
    Avg throughput per process             =  415198.52 kB/sec
    Min xfer                     = 5793792.00 kB

    Children see throughput for 18 random readers     = 7370460.28 kB/sec
    Parent sees throughput for 18 random readers     = 7370042.59 kB/sec
    Min throughput per process             =  354471.28 kB/sec 
    Max throughput per process             =  537200.56 kB/sec
    Avg throughput per process             =  409470.02 kB/sec
    Min xfer                     = 6919168.00 kB

    Children see throughput for 18 mixed workload     = 7557081.97 kB/sec
    Parent sees throughput for 18 mixed workload     = 5562355.09 kB/sec
    Min throughput per process             =  328829.50 kB/sec 
    Max throughput per process             =  528019.62 kB/sec
    Avg throughput per process             =  419837.89 kB/sec
    Min xfer                     = 6531072.00 kB

    Children see throughput for 18 random writers     = 7396597.97 kB/sec
    Parent sees throughput for 18 random writers     = 5062652.82 kB/sec
    Min throughput per process             =  388925.03 kB/sec 
    Max throughput per process             =  432092.16 kB/sec
    Avg throughput per process             =  410922.11 kB/sec
    Min xfer                     = 9444352.00 kB

    Children see throughput for 18 pwrite writers     = 8056269.75 kB/sec
    Parent sees throughput for 18 pwrite writers     = 4807351.59 kB/sec
    Min throughput per process             =  421969.41 kB/sec 
    Max throughput per process             =  482019.78 kB/sec
    Avg throughput per process             =  447570.54 kB/sec
    Min xfer                     = 9180160.00 kB

    Children see throughput for 18 pread readers     = 7454417.31 kB/sec
    Parent sees throughput for 18 pread readers     = 7454072.52 kB/sec
    Min throughput per process             =  364471.31 kB/sec 
    Max throughput per process             =  449894.91 kB/sec
    Avg throughput per process             =  414134.30 kB/sec
    Min xfer                     = 8495104.00 kB

    Children see throughput for 18 fwriters     = 5932789.12 kB/sec
    Parent sees throughput for 18 fwriters         = 4305918.28 kB/sec
    Min throughput per process             =  280836.97 kB/sec 
    Max throughput per process             =  361065.09 kB/sec
    Avg throughput per process             =  329599.40 kB/sec
    Min xfer                     = 10485760.00 kB

    Children see throughput for 18 freaders     = 8102682.31 kB/sec
    Parent sees throughput for 18 freaders         = 7731231.97 kB/sec
    Min throughput per process             =  429523.03 kB/sec 
    Max throughput per process             =  547695.06 kB/sec
    Avg throughput per process             =  450149.02 kB/sec
    Min xfer                     = 10485760.00 kB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 1024 kBytes "
"Output is in kBytes/sec"

"  Initial write " 8346941.12 

"        Rewrite " 8077831.41 

"           Read " 7529366.47 

"        Re-read " 7524155.94 

"   Reverse Read " 7555020.53 

"    Stride read " 7473573.38 

"    Random read " 7370460.28 

" Mixed workload " 7557081.97 

"   Random write " 7396597.97 

"         Pwrite " 8056269.75 

"          Pread " 7454417.31 

"         Fwrite " 5932789.12 

"          Fread " 8102682.31 


iozone test complete.

```
That was testing these two pools, where /KVM_Pool is datapool and /data is datapool
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v kpool
  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:01 with 0 errors on Mon May  8 02:17:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    kpool                                   ONLINE       0     0     0
      raidz2-0                              ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1     ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1     ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1     ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1     ONLINE       0     0     0
    logs    
      mirror-1                              ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part1  ONLINE       0     0     0
        nvme-PCIe_SSD_23011650000181-part2  ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000181-part3    ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 01:35:02 with 0 errors on Sun Apr  9 01:59:04 2023
config:

    NAME                                     STATE     READ WRITE CKSUM
    datapool                                 ONLINE       0     0     0
      ata-ST8000DM004-2U9188_ZR143PZD-part1  ONLINE       0     0     0
    logs    
      nvme-PCIe_SSD_23011650000183-part1     ONLINE       0     0     0
    cache
      nvme-PCIe_SSD_23011650000183-part3     ONLINE       0     0     0

errors: No known data errors

```
You can install iozone with:
```

sudo apt install iozone3

```

---

### Post by papriak on 2023-05-08
> **MAFoElffen said:**
> My CPU has 10 cores/20 threads...

I assume you're talking to 1Fallen, right?

My server's i7-4790 CPU has 4 cores/8 threads,so even if I had a pool comprised of NVMe SSDs I doubt I'd get results like yours.  :P

---

### Post by MAFoElffen on 2023-05-08
But if you changed -l and -u to 6, then did only 6 files, you could get and idea of what your total throughput is... And throughput for each thread. Just an idea.

I was just filling time and doing other things until those drives delivered. My datapool is HDD.

---

### Post by papriak on 2023-05-08
> **MAFoElffen said:**
> But if you changed -l and -u to 6, then did only 6 files, you could get and idea of what your total throughput is... And throughput for each thread. Just an idea.

I was just filling time and doing other things until those drives delivered. My datapool is HDD.

Fair point, here's what my results were:

```
server@server:~$ sudo iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
[sudo] password for server: 
        Iozone: Performance Test of File I/O
                Version $Revision: 3.489 $
                Compiled for 64 bit mode.
                Build: linux-AMD64 

        Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
                     Al Slater, Scott Rhine, Mike Wisner, Ken Goss
                     Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
                     Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
                     Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy, Dave Boone,
                     Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root,
                     Fabrice Bacchella, Zhenghua Xue, Qin Li, Darren Sawyer,
                     Vangel Bojaxhi, Ben England, Vikentsi Lapa,
                     Alexey Skidanov, Sudhir Kumar.

        Run began: Mon May  8 22:16:50 2023

        Excel chart generation enabled
        Record Size 1024 kB
        File size set to 10485760 kB
        Command line used: iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
        Output is in kBytes/sec
        Time Resolution = 0.000001 seconds.
        Processor cache size set to 1024 kBytes.
        Processor cache line size set to 32 bytes.
        File stride size set to 17 * record size.
        Min process = 6 
        Max process = 6 
        Throughput test with 6 processes
        Each process writes a 10485760 kByte file in 1024 kByte records

        Children see throughput for  6 initial writers  = 3004663.88 kB/sec
        Parent sees throughput for  6 initial writers   = 2600379.04 kB/sec
        Min throughput per process                      =  481569.94 kB/sec 
        Max throughput per process                      =  509491.75 kB/sec
        Avg throughput per process                      =  500777.31 kB/sec
        Min xfer                                        = 9914368.00 kB

        Children see throughput for  6 rewriters        = 2986456.47 kB/sec
        Parent sees throughput for  6 rewriters         = 2638490.05 kB/sec
        Min throughput per process                      =  474141.81 kB/sec 
        Max throughput per process                      =  515207.75 kB/sec
        Avg throughput per process                      =  497742.74 kB/sec
        Min xfer                                        = 9650176.00 kB

        Children see throughput for  6 readers          = 5820561.50 kB/sec
        Parent sees throughput for  6 readers           = 5820030.88 kB/sec
        Min throughput per process                      =  826601.69 kB/sec 
        Max throughput per process                      = 1205840.38 kB/sec
        Avg throughput per process                      =  970093.58 kB/sec
        Min xfer                                        = 7188480.00 kB

        Children see throughput for 6 re-readers        = 5815889.50 kB/sec
        Parent sees throughput for 6 re-readers         = 5815354.48 kB/sec
        Min throughput per process                      =  818068.69 kB/sec 
        Max throughput per process                      = 1296378.50 kB/sec
        Avg throughput per process                      =  969314.92 kB/sec
        Min xfer                                        = 6617088.00 kB

        Children see throughput for 6 reverse readers   = 5764039.06 kB/sec
        Parent sees throughput for 6 reverse readers    = 5763529.23 kB/sec
        Min throughput per process                      =  846085.06 kB/sec 
        Max throughput per process                      = 1149764.25 kB/sec
        Avg throughput per process                      =  960673.18 kB/sec
        Min xfer                                        = 7716864.00 kB

        Children see throughput for 6 stride readers    = 5687227.75 kB/sec
        Parent sees throughput for 6 stride readers     = 5686698.58 kB/sec
        Min throughput per process                      =  815622.88 kB/sec 
        Max throughput per process                      = 1242317.75 kB/sec
        Avg throughput per process                      =  947871.29 kB/sec
        Min xfer                                        = 6884352.00 kB

        Children see throughput for 6 random readers    = 5509549.06 kB/sec
        Parent sees throughput for 6 random readers     = 5508984.72 kB/sec
        Min throughput per process                      =  763531.19 kB/sec 
        Max throughput per process                      = 1265848.75 kB/sec
        Avg throughput per process                      =  918258.18 kB/sec
        Min xfer                                        = 6325248.00 kB

        Children see throughput for 6 mixed workload    = 5692642.56 kB/sec
        Parent sees throughput for 6 mixed workload     = 3688494.86 kB/sec
        Min throughput per process                      =  843491.56 kB/sec 
        Max throughput per process                      = 1057538.38 kB/sec
        Avg throughput per process                      =  948773.76 kB/sec
        Min xfer                                        = 8364032.00 kB

        Children see throughput for 6 random writers    = 2582926.62 kB/sec
        Parent sees throughput for 6 random writers     = 2203485.66 kB/sec
        Min throughput per process                      =  420695.84 kB/sec 
        Max throughput per process                      =  438500.41 kB/sec
        Avg throughput per process                      =  430487.77 kB/sec
        Min xfer                                        = 10060800.00 kB

        Children see throughput for 6 pwrite writers    = 2987456.19 kB/sec
        Parent sees throughput for 6 pwrite writers     = 2373081.55 kB/sec
        Min throughput per process                      =  485326.34 kB/sec 
        Max throughput per process                      =  518026.88 kB/sec
        Avg throughput per process                      =  497909.36 kB/sec
        Min xfer                                        = 9824256.00 kB

        Children see throughput for 6 pread readers     = 5758185.19 kB/sec
        Parent sees throughput for 6 pread readers      = 5757675.76 kB/sec
        Min throughput per process                      =  822803.81 kB/sec 
        Max throughput per process                      = 1213020.88 kB/sec
        Avg throughput per process                      =  959697.53 kB/sec
        Min xfer                                        = 7112704.00 kB

        Children see throughput for  6 fwriters         = 3077094.69 kB/sec
        Parent sees throughput for  6 fwriters          = 2614048.87 kB/sec
        Min throughput per process                      =  506202.03 kB/sec 
        Max throughput per process                      =  522564.78 kB/sec
        Avg throughput per process                      =  512849.11 kB/sec
        Min xfer                                        = 10485760.00 kB

        Children see throughput for  6 freaders         = 6358879.25 kB/sec
        Parent sees throughput for  6 freaders          = 5920911.74 kB/sec
        Min throughput per process                      =  986863.50 kB/sec 
        Max throughput per process                      = 1167864.75 kB/sec
        Avg throughput per process                      = 1059813.21 kB/sec
        Min xfer                                        = 10485760.00 kB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 1024 kBytes "
"Output is in kBytes/sec"

"  Initial write " 3004663.88 

"        Rewrite " 2986456.47 

"           Read " 5820561.50 

"        Re-read " 5815889.50 

"   Reverse Read " 5764039.06 

"    Stride read " 5687227.75 

"    Random read " 5509549.06 

" Mixed workload " 5692642.56 

"   Random write " 2582926.62 

"         Pwrite " 2987456.19 

"          Pread " 5758185.19 

"         Fwrite " 3077094.69 

"          Fread " 6358879.25 


iozone test complete.
```


If I'm reading that right, my transfer speeds shouldn't be going below 1GB/s...

But I have much to learn.  *shrug*

---

### Post by MAFoElffen on 2023-05-10
OK --

The new disks came and I continued my testing. For L2ARC, because "I" have 128GB, 

I multiplied by 10 and gave mine 128000GiB for L2ARC Cache. Yours would still be 320GiB.

For SLOG log cache, I set the partition on that 2TB drive to different sizes... Each size set, I would:
 - Add the partion to the pool.
 - Test with the fio comand we have been using for a Write Benchmark
 - Remove the partition from the pool
 - Reset the size of the partition, and go through it again...

What I found (for mine, on my datapool, which is HDD) was with SLOG size set at 1TiB, it got it's best throughput. Each side of that increasing or decreasing in size, the throughput fell off.

The warning I have:
Is to not change the size while the device is active on the pool. I found out "the hard way", zoning out between steps. It made the whole pool "Not Available", even for import until the same devices were all present in the pool (with that SLOG set back to the previous size). It was bad for a while. I had to straighten it out, then import that pool back in. I can make mistakes sometimes. Good thing I know enough on how to recover from them. LOL.

---

### Post by papriak on 2023-05-10
> **MAFoElffen said:**
> OK --

The new disks came and I continued my testing. For L2ARC, because "I" have 128GB, 

I multiplied by 10 and gave mine 128000GiB for L2ARC Cache. Yours would still be 320GiB.

For SLOG log cache, I set the partition on that 2TB drive to different sizes... Each size set, I would:
 - Add the partion to the pool.
 - Test with the fio comand we have been using for a Write Benchmark
 - Remove the partition from the pool
 - Reset the size of the partition, and go through it again...

What I found (for mine, on my datapool, which is HDD) was with SLOG size set at 1TiB, it got it's best throughput. Each side of that increasing or decreasing in size, the throughput fell off.

The warning I have:
Is to not change the size while the device is active on the pool. I found out "the hard way", zoning out between steps. It made the whole pool "Not Available", even for import until the same devices were all present in the pool (with that SLOG set back to the previous size). It was bad for a while. I had to straighten it out, then import that pool back in. I can make mistakes sometimes. Good thing I know enough on how to recover from them. LOL.

I'm glad I read your warning, just in the nick of time.  :lol:

I'm not sure if you meant 1TiB as in 1000GB or 1024GB though.  Thankfully my NVMe has room for both.

I'll test the results on both partitions and post my findings.  :)

---

### Post by papriak on 2023-05-10
1024GB:  30GB worth of MP4 files still starts transferring strong at 1GB/s from Windows for a few seconds, then falls to 500MB/s.

```
server@server:~$ sudo iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
[sudo] password for server: 
        Iozone: Performance Test of File I/O
                Version $Revision: 3.489 $
                Compiled for 64 bit mode.
                Build: linux-AMD64 

        Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
                     Al Slater, Scott Rhine, Mike Wisner, Ken Goss
                     Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
                     Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
                     Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy, Dave Boone,
                     Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root,
                     Fabrice Bacchella, Zhenghua Xue, Qin Li, Darren Sawyer,
                     Vangel Bojaxhi, Ben England, Vikentsi Lapa,
                     Alexey Skidanov, Sudhir Kumar.

        Run began: Thu May 11 02:34:43 2023

        Excel chart generation enabled
        Record Size 1024 kB
        File size set to 10485760 kB
        Command line used: iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
        Output is in kBytes/sec
        Time Resolution = 0.000001 seconds.
        Processor cache size set to 1024 kBytes.
        Processor cache line size set to 32 bytes.
        File stride size set to 17 * record size.
        Min process = 6 
        Max process = 6 
        Throughput test with 6 processes
        Each process writes a 10485760 kByte file in 1024 kByte records

        Children see throughput for  6 initial writers  = 3181241.00 kB/sec
        Parent sees throughput for  6 initial writers   = 2882106.52 kB/sec
        Min throughput per process                      =  523339.31 kB/sec 
        Max throughput per process                      =  542362.44 kB/sec
        Avg throughput per process                      =  530206.83 kB/sec
        Min xfer                                        = 10118144.00 kB

        Children see throughput for  6 rewriters        = 3172124.28 kB/sec
        Parent sees throughput for  6 rewriters         = 2648258.90 kB/sec
        Min throughput per process                      =  518954.12 kB/sec 
        Max throughput per process                      =  559510.44 kB/sec
        Avg throughput per process                      =  528687.38 kB/sec
        Min xfer                                        = 9726976.00 kB

        Children see throughput for  6 readers          = 5527910.75 kB/sec
        Parent sees throughput for  6 readers           = 5527523.46 kB/sec
        Min throughput per process                      =  743480.44 kB/sec 
        Max throughput per process                      = 1036673.88 kB/sec
        Avg throughput per process                      =  921318.46 kB/sec
        Min xfer                                        = 7520256.00 kB

        Children see throughput for 6 re-readers        = 5547468.38 kB/sec
        Parent sees throughput for 6 re-readers         = 5546988.16 kB/sec
        Min throughput per process                      =  751015.38 kB/sec 
        Max throughput per process                      = 1196087.88 kB/sec
        Avg throughput per process                      =  924578.06 kB/sec
        Min xfer                                        = 6584320.00 kB

        Children see throughput for 6 reverse readers   = 5769691.31 kB/sec
        Parent sees throughput for 6 reverse readers    = 5769327.54 kB/sec
        Min throughput per process                      =  821549.56 kB/sec 
        Max throughput per process                      = 1068822.00 kB/sec
        Avg throughput per process                      =  961615.22 kB/sec
        Min xfer                                        = 8059904.00 kB

        Children see throughput for 6 stride readers    = 5656307.94 kB/sec
        Parent sees throughput for 6 stride readers     = 5655873.93 kB/sec
        Min throughput per process                      =  777072.19 kB/sec 
        Max throughput per process                      = 1113091.50 kB/sec
        Avg throughput per process                      =  942717.99 kB/sec
        Min xfer                                        = 7320576.00 kB

        Children see throughput for 6 random readers    = 5465129.25 kB/sec
        Parent sees throughput for 6 random readers     = 5464711.14 kB/sec
        Min throughput per process                      =  756808.38 kB/sec 
        Max throughput per process                      = 1079407.88 kB/sec
        Avg throughput per process                      =  910854.88 kB/sec
        Min xfer                                        = 7352320.00 kB

        Children see throughput for 6 mixed workload    = 5482796.81 kB/sec
        Parent sees throughput for 6 mixed workload     = 3905748.00 kB/sec
        Min throughput per process                      =  856841.88 kB/sec 
        Max throughput per process                      =  990489.00 kB/sec
        Avg throughput per process                      =  913799.47 kB/sec
        Min xfer                                        = 9071616.00 kB

        Children see throughput for 6 random writers    = 2829858.06 kB/sec
        Parent sees throughput for 6 random writers     = 2361913.94 kB/sec
        Min throughput per process                      =  459331.75 kB/sec 
        Max throughput per process                      =  487141.72 kB/sec
        Avg throughput per process                      =  471643.01 kB/sec
        Min xfer                                        = 9887744.00 kB

        Children see throughput for 6 pwrite writers    = 3015499.88 kB/sec
        Parent sees throughput for 6 pwrite writers     = 2370274.06 kB/sec
        Min throughput per process                      =  482596.69 kB/sec 
        Max throughput per process                      =  532022.81 kB/sec
        Avg throughput per process                      =  502583.31 kB/sec
        Min xfer                                        = 9511936.00 kB

        Children see throughput for 6 pread readers     = 5616423.06 kB/sec
        Parent sees throughput for 6 pread readers      = 5615985.75 kB/sec
        Min throughput per process                      =  807784.81 kB/sec 
        Max throughput per process                      = 1224952.38 kB/sec
        Avg throughput per process                      =  936070.51 kB/sec
        Min xfer                                        = 6915072.00 kB

        Children see throughput for  6 fwriters         = 3062635.97 kB/sec
        Parent sees throughput for  6 fwriters          = 2540664.05 kB/sec
        Min throughput per process                      =  496122.94 kB/sec 
        Max throughput per process                      =  541153.81 kB/sec
        Avg throughput per process                      =  510439.33 kB/sec
        Min xfer                                        = 10485760.00 kB

        Children see throughput for  6 freaders         = 5843791.31 kB/sec
        Parent sees throughput for  6 freaders          = 5629064.84 kB/sec
        Min throughput per process                      =  938211.31 kB/sec 
        Max throughput per process                      = 1075018.25 kB/sec
        Avg throughput per process                      =  973965.22 kB/sec
        Min xfer                                        = 10485760.00 kB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 1024 kBytes "
"Output is in kBytes/sec"

"  Initial write " 3181241.00 

"        Rewrite " 3172124.28 

"           Read " 5527910.75 

"        Re-read " 5547468.38 

"   Reverse Read " 5769691.31 

"    Stride read " 5656307.94 

"    Random read " 5465129.25 

" Mixed workload " 5482796.81 

"   Random write " 2829858.06 

"         Pwrite " 3015499.88 

"          Pread " 5616423.06 

"         Fwrite " 3062635.97 

"          Fread " 5843791.31 


iozone test complete.
```


1000GB:  The Windows transfer doesn't seem to have changed this time either.

```
server@server:~$ sudo iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
        Iozone: Performance Test of File I/O
                Version $Revision: 3.489 $
                Compiled for 64 bit mode.
                Build: linux-AMD64 

        Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
                     Al Slater, Scott Rhine, Mike Wisner, Ken Goss
                     Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
                     Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
                     Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy, Dave Boone,
                     Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root,
                     Fabrice Bacchella, Zhenghua Xue, Qin Li, Darren Sawyer,
                     Vangel Bojaxhi, Ben England, Vikentsi Lapa,
                     Alexey Skidanov, Sudhir Kumar.

        Run began: Thu May 11 03:03:44 2023

        Excel chart generation enabled
        Record Size 1024 kB
        File size set to 10485760 kB
        Command line used: iozone -R -l 6 -u 6 -r 1m -s 10g -F /Pool/Backups/f1 /Pool/Backups/f2 /Pool/Backups/f3 /Pool/Backups/f4 /Pool/Backups/f5 /Pool/Backups/f6 /Pool/Backups/f7 /Pool/Backups/f8
        Output is in kBytes/sec
        Time Resolution = 0.000001 seconds.
        Processor cache size set to 1024 kBytes.
        Processor cache line size set to 32 bytes.
        File stride size set to 17 * record size.
        Min process = 6 
        Max process = 6 
        Throughput test with 6 processes
        Each process writes a 10485760 kByte file in 1024 kByte records

        Children see throughput for  6 initial writers  = 3507348.19 kB/sec
        Parent sees throughput for  6 initial writers   = 3058278.19 kB/sec
        Min throughput per process                      =  565955.19 kB/sec 
        Max throughput per process                      =  612601.31 kB/sec
        Avg throughput per process                      =  584558.03 kB/sec
        Min xfer                                        = 9688064.00 kB

        Children see throughput for  6 rewriters        = 3481944.88 kB/sec
        Parent sees throughput for  6 rewriters         = 3029154.23 kB/sec
        Min throughput per process                      =  562375.38 kB/sec 
        Max throughput per process                      =  603074.12 kB/sec
        Avg throughput per process                      =  580324.15 kB/sec
        Min xfer                                        = 9778176.00 kB

        Children see throughput for  6 readers          = 5598253.19 kB/sec
        Parent sees throughput for  6 readers           = 5597805.81 kB/sec
        Min throughput per process                      =  771621.50 kB/sec 
        Max throughput per process                      = 1090802.38 kB/sec
        Avg throughput per process                      =  933042.20 kB/sec
        Min xfer                                        = 7417856.00 kB

        Children see throughput for 6 re-readers        = 5828998.75 kB/sec
        Parent sees throughput for 6 re-readers         = 5828393.86 kB/sec
        Min throughput per process                      =  731320.75 kB/sec 
        Max throughput per process                      = 1378394.88 kB/sec
        Avg throughput per process                      =  971499.79 kB/sec
        Min xfer                                        = 5563392.00 kB

        Children see throughput for 6 reverse readers   = 5857969.38 kB/sec
        Parent sees throughput for 6 reverse readers    = 5857432.51 kB/sec
        Min throughput per process                      =  729061.06 kB/sec 
        Max throughput per process                      = 1254581.25 kB/sec
        Avg throughput per process                      =  976328.23 kB/sec
        Min xfer                                        = 6093824.00 kB

        Children see throughput for 6 stride readers    = 5721219.69 kB/sec
        Parent sees throughput for 6 stride readers     = 5720783.62 kB/sec
        Min throughput per process                      =  777626.06 kB/sec 
        Max throughput per process                      = 1305605.00 kB/sec
        Avg throughput per process                      =  953536.61 kB/sec
        Min xfer                                        = 6245376.00 kB

        Children see throughput for 6 random readers    = 5548749.62 kB/sec
        Parent sees throughput for 6 random readers     = 5548267.86 kB/sec
        Min throughput per process                      =  777538.81 kB/sec 
        Max throughput per process                      = 1175295.00 kB/sec
        Avg throughput per process                      =  924791.60 kB/sec
        Min xfer                                        = 6937600.00 kB

        Children see throughput for 6 mixed workload    = 5663897.00 kB/sec
        Parent sees throughput for 6 mixed workload     = 4247968.95 kB/sec
        Min throughput per process                      =  881531.69 kB/sec 
        Max throughput per process                      = 1037206.62 kB/sec
        Avg throughput per process                      =  943982.83 kB/sec
        Min xfer                                        = 8916992.00 kB

        Children see throughput for 6 random writers    = 3009773.06 kB/sec
        Parent sees throughput for 6 random writers     = 2457354.25 kB/sec
        Min throughput per process                      =  480760.72 kB/sec 
        Max throughput per process                      =  515941.03 kB/sec
        Avg throughput per process                      =  501628.84 kB/sec
        Min xfer                                        = 9774080.00 kB

        Children see throughput for 6 pwrite writers    = 3074151.00 kB/sec
        Parent sees throughput for 6 pwrite writers     = 2444515.52 kB/sec
        Min throughput per process                      =  495892.94 kB/sec 
        Max throughput per process                      =  530449.81 kB/sec
        Avg throughput per process                      =  512358.50 kB/sec
        Min xfer                                        = 9802752.00 kB

        Children see throughput for 6 pread readers     = 5268382.81 kB/sec
        Parent sees throughput for 6 pread readers      = 5268058.31 kB/sec
        Min throughput per process                      =  704379.56 kB/sec 
        Max throughput per process                      = 1031292.62 kB/sec
        Avg throughput per process                      =  878063.80 kB/sec
        Min xfer                                        = 7161856.00 kB

        Children see throughput for  6 fwriters         = 3043619.78 kB/sec
        Parent sees throughput for  6 fwriters          = 2573651.05 kB/sec
        Min throughput per process                      =  497009.31 kB/sec 
        Max throughput per process                      =  520607.19 kB/sec
        Avg throughput per process                      =  507269.96 kB/sec
        Min xfer                                        = 10485760.00 kB

        Children see throughput for  6 freaders         = 6515599.38 kB/sec
        Parent sees throughput for  6 freaders          = 5934045.00 kB/sec
        Min throughput per process                      =  989042.50 kB/sec 
        Max throughput per process                      = 1329486.38 kB/sec
        Avg throughput per process                      = 1085933.23 kB/sec
        Min xfer                                        = 10485760.00 kB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 1024 kBytes "
"Output is in kBytes/sec"

"  Initial write " 3507348.19 

"        Rewrite " 3481944.88 

"           Read " 5598253.19 

"        Re-read " 5828998.75 

"   Reverse Read " 5857969.38 

"    Stride read " 5721219.69 

"    Random read " 5548749.62 

" Mixed workload " 5663897.00 

"   Random write " 3009773.06 

"         Pwrite " 3074151.00 

"          Pread " 5268382.81 

"         Fwrite " 3043619.78 

"          Fread " 6515599.38 


iozone test complete.
```



Do you see any major differences?

---

### Post by MAFoElffen on 2023-05-11
No major differences. I did it in GiB's not GB. It seems like yours did better at 1000GiB, by a small margin.

In my tests, I did those in 100GiBs increments and ran:
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
Three times with each setting, and took the averages of the 3 tests for each cache size. That way I could find the sweet spot, where I chose what came out as the best size for my hardware.

I did run iozone again to see what the differences where... But since we had all that data for the baseline with fio, I used that to continue the tests. 

I ended up with this as the best results I got, for a 1000GiB SLOG cache...
```

  WRITE: bw=664MiB/s (697MB/s), 664MiB/s-664MiB/s (697MB/s-697MB/s), io=10.0GiB (10.7GB), run=15412-15412msec
  WRITE: bw=733MiB/s (768MB/s), 733MiB/s-733MiB/s (768MB/s-768MB/s), io=10.0GiB (10.7GB), run=13974-13974msec
  WRITE: bw=666MiB/s (698MB/s), 666MiB/s-666MiB/s (698MB/s-698MB/s), io=10.0GiB (10.7GB), run=15381-15381msec

```
Which averages out to a write of 721MB/s. I think the differences with mine, compared to yours is more CPU (i9 gen 10 vs. i7 gen 4), and a newer Motherboard (chipsets B460 vs. Z97), with the differences in the PCIe slots and PCIe lane counts...
RE:
 [https://www.intel.com/content/www/us/en/products/sku/201841/intel-b460-chipset/specifications.html](https://www.intel.com/content/www/us/en/products/sku/201841/intel-b460-chipset/specifications.html)
 [https://ark.intel.com/content/www/us/en/ark/products/82012/intel-z97-chipset.html](https://ark.intel.com/content/www/us/en/ark/products/82012/intel-z97-chipset.html)

I think for your hardware, it seems to be tuned now. I am impressed that it came up so far... I think the number of drives in the pool really factored in there for you.

---

### Post by papriak on 2023-05-11
> **MAFoElffen said:**
> I think for your hardware, it seems to be tuned now. I am impressed that it came up so far... I think the number of drives in the pool really factored in there for you.

Yes, my server's hardware is somewhat dated.  I'd like to upgrade to a motherboard that can take ECC memory at some point, but that won't be for a while.


Are you sure there's no way for my server's 2TB NMVe drive to take all the incoming data at 1GB/s until the pool catches up?

If there isn't,  I think I'll change that drive back to a network share and use a 1TB SATAIII SSD for the Pool's SLOG;  Then I can copy the data from the NVMe to the pool, have a copy on the NVMe in case there's an error, and get back to my games on the Windows PC quicker.  :P

---

### Post by MAFoElffen on 2023-05-11
My tests showed that, at least with mine, that with more than 1TiB, that the speed fell off. You might want to vary yours up and down from that by 100MiB and see if that is the same with yours, before you do that to confirm with your hardware.

Remember that before my tests, that the Doc's and common thoughts by people recommended that SLOG should be 16GB to 64GB. Before, I had just accepted that as the truth.

---

### Post by papriak on 2023-05-11
> **MAFoElffen said:**
> My tests showed that, at least with mine, that with more than 1TiB, that the speed fell off. You might want to vary yours up and down from that by 100MiB and see if that is the same with yours, before you do that to confirm with your hardware.

Remember that before my tests, that the Doc's and common thoughts by people recommended that SLOG should be 16GB to 64GB. Before, I had just accepted that as the truth.

Sure, I have nothing to lose.

And they probably didn't have as many CPU cores and NVMes as you do either.  :P

---

### Post by papriak on 2023-05-11
> **MAFoElffen said:**
> My tests showed that, at least with mine, that with more than 1TiB, that the speed fell off. You might want to vary yours up and down from that by 100MiB and see if that is the same with yours, before you do that to confirm with your hardware.

Remember that before my tests, that the Doc's and common thoughts by people recommended that SLOG should be 16GB to 64GB. Before, I had just accepted that as the truth.

900GB - Windows transfer started at 450MB/s, went up to nearly 700MB/s, then averaged 500 again.

875GB - Averaged 400MB/s...

850GB - Windows transfer started at 450MB/s, almost sustained 600MB/s for 5-10 seconds, then slowed to 500MB/s average.

825GB - Windows transfer peaked at 700MB/s early on, but averaged slower sustained writes, maybe 450MB/s.

800GB - Windows transfer started at 600MB/s and ramped down to 500MB/s more slowly than before.

800GB retry:  Averaged upper 400's after a 1GB/s start

775GB - Started at 1GB, quickly averaged 500.

750GB - Starts at 700, dips to 450, then averages 500.

725GB:  Started at 1GB/s for a few seconds then fell to upper 400's.

700GB - Windows started at about 650MB/s, went down for a few seconds,  the back up to 600 for a few more seconds, then averaged at 500.

700GB retry - Started at 1GB, slowly went down to 500.

675GB - Started at 1GB for a few seconds, then down to upper 400s.



Doesn't look like I can sustain 1GB/s nor 600MB/s.

 I'm out of time for now, May I ask you think I should do when I get back later?

---

### Post by papriak on 2023-05-11
Update:

I just realized that my NVMe drive is QLC, so that may be holding it back...


Edit:  I re-instated the other 500GB SATA SSD as the SLOG and I'm getting 1GB/s at the beginning, then it slows to about 500MB/s.  Just like the NVMe drive.

---

### Post by MAFoElffen on 2023-05-12
QLC? Dang, LOL So what is that drive rated at for writes. (Usually focus on them is reads.)

Yes, you did the right thing. Surprised that your stats were the same with the SATA SSD.

---

### Post by papriak on 2023-05-12
> **MAFoElffen said:**
> QLC? Dang, LOL So what is that drive rated at for writes. (Usually focus on them is reads.)

Yes, you did the right thing. Surprised that your stats were the same with the SATA SSD.

Can't seem to get a definite answer for write rates after the cache is used up, but here's a chart from Tom's Hardware.

Mine's the Intel 660p, in case it's not obvious.  :P

[https://cdn.mos.cms.futurecdn.net/agNM98TwXqp9xukaqDXj9Z-970-80.png.webp](https://cdn.mos.cms.futurecdn.net/agNM98TwXqp9xukaqDXj9Z-970-80.png.webp)

---

### Post by MAFoElffen on 2023-05-12
Wow! That sucks. LOL

From that chart, I would think that your SATA SSD has better write speeds than that for sustained writes than your NVMe drive. 

From your test results... It looks like for the size of the SLOG cache, your system was happy with 750GB to 1TB. You know that it 'should' be better with a faster drive for the cache. 

Though 500MB/s sustained writes over a network connection for 30GB of data is still great. Especially over what you were getting.

Has me thinking again.

---

### Post by papriak on 2023-05-12
> **MAFoElffen said:**
> Though 500MB/s sustained writes over a network connection for 30GB of data is still great. Especially over what you were getting.

Has me thinking again.

Oh?  What's on your mind?

---

### Post by MAFoElffen on 2023-05-12
I want to thank you for challenging me with this thread... Helping you with this has taught me a lot about challenging what is known, and especially for paying attention to the technologies that drives are using and the spec's expected from those. 

Not all "deals" save you money, if they do not perform to what you need, or expect.

I forgot that QLC and M.2 NGFF SATA drives were still around. I guess I need to try (harder) to not assume some of those details. Drives are not all created equal.

---

### Post by #&amp;thj^% on 2023-05-12
> **MAFoElffen said:**
> I want to thank you for challenging me with this thread... Helping you with this has taught me a lot about challenging what is known, and especially for paying attention to the technologies that drives are using and the spec's expected from those. 

Not all "deals" save you money, if they do not perform to what you need, or expect.

I forgot that QLC and M.2 NGFF SATA drives were still around. I guess I need to try (harder) to not assume some of those details. Drives are not all created equal.
+1 This one only gets 1/2 of the write speed. (Not the same machine used in all my previous posts)
```
Run status group 0 (all jobs):
  WRITE: bw=654MiB/s (686MB/s), 654MiB/s-654MiB/s (686MB/s-686MB/s), io=10.0GiB (10.7GB), run=15650-15650msec

```
AMD to Intel here:
```
inxi -Cxxxx
CPU:
  Info: quad core model: Intel Core i5-10210U bits: 64 type: MT MCP
    smt: enabled arch: Comet/Whiskey Lake note: check rev: C cache: L1: 256 KiB
    L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 3000 high: 3900 min/max: 400/4200 cores: 1: 3900 2: 2100
    3: 3900 4: 3900 5: 2100 6: 2100 7: 2100 8: 3900 bogomips: 33615
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx

```

QLC SSDs can store more data than TLC SSDs and they also cost less. However, they don&#8217;t perform as well or last as long, and they can be more error-prone. TLC SSDs perform better and last longer than QLC SSDs but store less data and cost more. 

It&#8217;s very important to keep in mind that the quality of SSDs can vary greatly from manufacturer to manufacturer, and also that your needs should drive your choices.

---

### Post by papriak on 2023-05-12
> **MAFoElffen said:**
> I want to thank you for challenging me with this thread... Helping you with this has taught me a lot about challenging what is known, and especially for paying attention to the technologies that drives are using and the spec's expected from those. 

Not all "deals" save you money, if they do not perform to what you need, or expect.

I forgot that QLC and M.2 NGFF SATA drives were still around. I guess I need to try (harder) to not assume some of those details. Drives are not all created equal.

Indeed, I was about to upgrade to 4TB NVMe models last night, then I realized they were QLC as well.

I suppose the "$200 each" deals really were too good to be true.

I suspect that offloading the SLOG to a SATA SSD which can keep up with the spinning drives will do, or perhaps to a pair of SSDs in RAID 0.

---

### Post by MAFoElffen on 2023-05-12
Yes. I think, beyond that, you are capped by the technology of the rest of your hardware. Especially your Z79 chipset and the hardware it supports. I read that ASUS Z79 boards, that if you use a Samsung 970 EVO M.2 NVMe, (3.0x4), that because of the Chipset, you will never get the true throughput of the drive through it... Because of the Z79 chipset and it's older technology. The drive will work (because of backward compatibility), but not to it's potential. (Sorry about that.) I think you are saturated in the Lanes. 

I don't think much else you can do will make a major change to that, unless you went to a newer motherboard. I think you've stretched those limits fairly well. (LOL) Good job at that.

Like when people ask me what would make the most sense in an upgrade for Gaming... First --> "GPU" ... For Storage, is Bandwidth and Lanes.

---

### Post by papriak on 2023-05-12
> **MAFoElffen said:**
> Yes. I think, beyond that, you are capped by the technology of the rest of your hardware. Especially your Z79 chipset and the hardware it supports.

I don't think much else you can do will make a major change to that, unless you went to a newer motherboard. I think you've stretched those limits fairly well. (LOL) Good job at that.

Like when people ask me what would make the most sense in an upgrade for Gaming... First --> "GPU" ... For Storage, is Bandwidth and Lanes.

Alright then, I'll consider this thread closed.

Thank you both very much for assisting me.  :)

---

