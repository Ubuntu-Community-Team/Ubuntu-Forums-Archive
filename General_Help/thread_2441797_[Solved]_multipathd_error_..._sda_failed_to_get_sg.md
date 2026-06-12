---
title: "[Solved] multipathd error ... sda: failed to get sgio uid: No such file or directory"
date: 2020-04-26
forum: General Help
---

### Post by jg3 on 2020-04-26
Hi,
I'm running Ubuntu Server 20.04 ... it's not my first but I'm probably still more comfortable with *BSD.   That said, I'm having a good time with it when I see my syslog is filling up with messages from multipathd...

```
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: add missing path
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get sysfs uid: Invalid argument
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get sgio uid: No such file or directory
```

This is happening every five seconds, and it's not only annoying, it's worrisome.

My server is a virtual machine on ESXi 6.7 ... and I gave it 50 GB of virtual disk at install and selected to use LVM.

Any hints on what this means and how to solve it?    For example, what is sgio and what does it have to do with sda?



Here are a few more points that may be germane:


```
$ sudo fdisk -l
<...snip...>

Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2594FF21-D82C-4B56-8CD6-9E352E48770A

Device       Start       End   Sectors Size Type
/dev/sda1     2048      4095      2048   1M BIOS boot
/dev/sda2     4096   2101247   2097152   1G Linux filesystem
/dev/sda3  2101248 104855551 102754304  49G Linux filesystem

<...snip...>
```


```
$ cat /etc/multipath.conf
defaults {
    user_friendly_names yes
}
```

```
$ sudo multipath -t
          [FONT=Menlo]defaults {[/FONT]
  [FONT=Menlo]        verbosity 2[/FONT]
  [FONT=Menlo]        polling_interval 5[/FONT]
  [FONT=Menlo]        max_polling_interval 20[/FONT]
  [FONT=Menlo]        reassign_maps "no"[/FONT]
  [FONT=Menlo]        multipath_dir "//lib/multipath"[/FONT]
  [FONT=Menlo]        path_selector "service-time 0"[/FONT]
  [FONT=Menlo]        path_grouping_policy "failover"[/FONT]
  [FONT=Menlo]        uid_attribute "ID_SERIAL"[/FONT]
  [FONT=Menlo]        prio "const"[/FONT]
  [FONT=Menlo]        prio_args ""[/FONT]
  [FONT=Menlo]        features "0"[/FONT]
  [FONT=Menlo]        path_checker "tur"[/FONT]
  [FONT=Menlo]        alias_prefix "mpath"[/FONT]
  [FONT=Menlo]        failback "manual"[/FONT]
  [FONT=Menlo]        rr_min_io 1000[/FONT]
  [FONT=Menlo]        rr_min_io_rq 1[/FONT]
  [FONT=Menlo]        max_fds "max"[/FONT]
  [FONT=Menlo]        rr_weight "uniform"[/FONT]
  [FONT=Menlo]        queue_without_daemon "no"[/FONT]
  [FONT=Menlo]        flush_on_last_del "no"[/FONT]
  [FONT=Menlo]        user_friendly_names "no"[/FONT]
  [FONT=Menlo]        fast_io_fail_tmo 5[/FONT]
  [FONT=Menlo]        bindings_file "/etc/multipath/bindings"[/FONT]
  [FONT=Menlo]        wwids_file "/etc/multipath/wwids"[/FONT]
  [FONT=Menlo]        prkeys_file "/etc/multipath/prkeys"[/FONT]
  [FONT=Menlo]        log_checker_err always[/FONT]
  [FONT=Menlo]        all_tg_pt "no"[/FONT]
  [FONT=Menlo]        retain_attached_hw_handler "yes"[/FONT]
  [FONT=Menlo]        detect_prio "yes"[/FONT]
  [FONT=Menlo]        detect_checker "yes"[/FONT]
  [FONT=Menlo]        force_sync "no"[/FONT]
  [FONT=Menlo]        strict_timing "no"[/FONT]
  [FONT=Menlo]        deferred_remove "no"[/FONT]
  [FONT=Menlo]        config_dir "/etc/multipath/conf.d"[/FONT]
  [FONT=Menlo]        delay_watch_checks "no"[/FONT]
  [FONT=Menlo]        delay_wait_checks "no"[/FONT]
  [FONT=Menlo]        san_path_err_threshold "no"[/FONT]
  [FONT=Menlo]        san_path_err_forget_rate "no"[/FONT]
  [FONT=Menlo]        san_path_err_recovery_time "no"[/FONT]
  [FONT=Menlo]        marginal_path_err_sample_time "no"[/FONT]
  [FONT=Menlo]        marginal_path_err_rate_threshold "no"[/FONT]
  [FONT=Menlo]        marginal_path_err_recheck_gap_time "no"[/FONT]
  [FONT=Menlo]        marginal_path_double_failed_time "no"[/FONT]
  [FONT=Menlo]        find_multipaths "on"[/FONT]
  [FONT=Menlo]        uxsock_timeout 4000[/FONT]
  [FONT=Menlo]        retrigger_tries 0[/FONT]
  [FONT=Menlo]        retrigger_delay 10[/FONT]
  [FONT=Menlo]        missing_uev_wait_timeout 30[/FONT]
  [FONT=Menlo]        skip_kpartx "no"[/FONT]
  [FONT=Menlo]        disable_changed_wwids ignored[/FONT]
  [FONT=Menlo]        remove_retries 0[/FONT]
  [FONT=Menlo]        ghost_delay "no"[/FONT]
  [FONT=Menlo]        find_multipaths_timeout -10[/FONT]
  [FONT=Menlo]        enable_foreign ""[/FONT]
  [FONT=Menlo]        marginal_pathgroups "no"[/FONT]
  [FONT=Menlo]}[/FONT]
  [FONT=Menlo]blacklist {[/FONT]
  [FONT=Menlo]...[/FONT]
      

```



```
$ cat /var/log/syslog | grep multipathd | head -33
Apr 26 16:09:52 ubuntu2004 multipathd[728]: --------start up--------
Apr 26 16:09:52 ubuntu2004 multipathd[728]: read /etc/multipath.conf
Apr 26 16:09:52 ubuntu2004 multipathd[728]: path checkers start up
Apr 26 16:09:52 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:09:52 ubuntu2004 multipathd[728]: sda: failed to get unknown uid: Invalid argument
Apr 26 16:09:52 ubuntu2004 kernel: [    5.758757] systemd[1]: Listening on multipathd control socket.
Apr 26 16:09:53 ubuntu2004 multipathd[728]: sda: triggering change event to reinitialize
Apr 26 16:09:53 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:09:53 ubuntu2004 multipathd[728]: sda: failed to get unknown uid: Invalid argument
Apr 26 16:09:53 ubuntu2004 multipathd[728]: sda: failed to get path uid
Apr 26 16:09:53 ubuntu2004 multipathd[728]: uevent trigger error
Apr 26 16:10:03 ubuntu2004 multipathd[728]: sda: triggering change event to reinitialize
Apr 26 16:10:03 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:10:03 ubuntu2004 multipathd[728]: sda: failed to get unknown uid: Invalid argument
Apr 26 16:10:03 ubuntu2004 multipathd[728]: sda: failed to get path uid
Apr 26 16:10:03 ubuntu2004 multipathd[728]: uevent trigger error
Apr 26 16:10:13 ubuntu2004 multipathd[728]: sda: triggering change event to reinitialize
Apr 26 16:10:13 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:10:13 ubuntu2004 multipathd[728]: sda: failed to get sysfs uid: Invalid argument
Apr 26 16:10:13 ubuntu2004 multipathd[728]: sda: failed to get sgio uid: No such file or directory
Apr 26 16:10:13 ubuntu2004 multipathd[728]: sda: failed to get path uid
Apr 26 16:10:13 ubuntu2004 multipathd[728]: uevent trigger error
Apr 26 16:10:23 ubuntu2004 multipathd[728]: sda: not initialized after 3 udev retriggers
Apr 26 16:10:24 ubuntu2004 multipathd[728]: sda: add missing path
Apr 26 16:10:24 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:10:24 ubuntu2004 multipathd[728]: sda: failed to get sysfs uid: Invalid argument
Apr 26 16:10:24 ubuntu2004 multipathd[728]: sda: failed to get sgio uid: No such file or directory
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: add missing path
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get udev uid: Invalid argument
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get sysfs uid: Invalid argument
Apr 26 16:10:29 ubuntu2004 multipathd[728]: sda: failed to get sgio uid: No such file or directory
<... and so on every 5 seconds ...>
```


Thank you!

--jg

---

### Post by vaeden on 2020-04-27
I had the same issue and following the steps in this article resolved it for me. [https://www.suse.com/support/kb/doc/?id=000016951](https://www.suse.com/support/kb/doc/?id=000016951)
Afterward, the disk appeared in /dev/disk/by-id

---

### Post by jg3 on 2020-04-27
Wow, thanks.  That worked and I would never have thought or found that based on my searches.  I'm new here, is there a way to mark the question solved or something?



From that page, here were the instructions I followed:

**Situation**

                                                                                      There is no link in [FONT=Courier New]/dev/disk/by-id[/FONT] for SCSI (sdx) devices. The OS is running as a guest on VMWare ESX
                                         
                                                                                                                  **Resolution**

                                                                                      By default VMWare doesn't provide information needed by [FONT=Courier New]udev[/FONT] to generate [FONT=Courier New]/dev/disk/by-id[/FONT]. This can be done by setting the following:
   
[LIST=1]
[*][LEFT]Start the vSphere Client, and log in to a vCenter Server.[/LEFT]
 
[*][LEFT]Select Virtual Machines and Templates and click the Virtual Machines tab.[/LEFT]
 
[*][LEFT]Right-click the virtual machine for which you are enabling the disk UUID attribute, and select Power > Power Off.[/LEFT]
    [LEFT]The virtual machine powers off.[/LEFT]
 
[*][LEFT]Right-click the virtual machine, and click Edit Settings.[/LEFT]
 
[*][LEFT]Click the Options tab, and select the General entry in the settings column.[/LEFT]
 
[*][LEFT]Click Configuration Parameters. The Configuration Parameters window appears.[/LEFT]
 
[*][LEFT]Click Add Row.[/LEFT]
 
[*][LEFT]In the Name column, enter [FONT=Courier New]disk.EnableUUID[/FONT].[/LEFT]
 
[*][LEFT]In the Value column, enter [FONT=Courier New]TRUE[/FONT].[/LEFT]
 
[*][LEFT]Click OK and click Save.[/LEFT]
 
[*][LEFT]Power on the virtual machine.[/LEFT]
 
[/LIST]

---

### Post by vaeden on 2020-04-27
Glad it worked for you also, and I derno, I'm new here too. :D I guess you just change the title as you did.

---

### Post by gorja239 on 2020-05-04
worked for me. thanks a lot!

---

### Post by dbrossard on 2020-05-04
There is another option I had to use. I have a Virtual Server running in a popular cheap cloud provider that uses ESX so I am unable to get to the vCenter console. I only have access to the command line on my virtual server. 
To solve this without access to the VM Host you can blacklist sda in the multipath.conf file. Here is my /etc/multipath.conf files contents which also blacklists common other devices like CDRom drives etc. that should never be checked for multipath configurations:

```

defaults {
    user_friendly_names yes
}
blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st|sda)[0-9]*"
}

```

I don't use any multipath (most VMs don't) but if you do, this will be different for you.

---

### Post by gwijsman on 2020-05-31
confirm solution of adding:

In the Name column, enter disk.EnableUUID.In the Value column, enter TRUE.

I used the web ui of esxi directly
* edit virtual machine settings
* VM options
* Advanced
* at Configuration Parameters press Edit Configuration...
add the key and value as described above
(VM Machine Power should be off)

---

### Post by baetard on 2021-04-26
Thanks. Editing the ESXi parameters did not solve the problem for me but using your conf file did.

---

