---
title: "chkrootkit - deletions??"
date: 2005-04-25
forum: General Help
---

### Post by dolson on 2005-04-25
When I run chkrootkit, I see these lines:

8 deletion(s) between Mon Apr 18 06:57:19 2005 and Sat May  4 09:12:17 2024
2 deletion(s) between Mon Apr 18 07:07:31 2005 and Sat May  8 08:38:55 1999
6 deletion(s) between Sun Aug 20 09:10:13 1995 and Wed May 17 19:42:28 2023

What on earth is that about? Here is that portion in context:

--snip--
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... nothing detected
Checking `rexedcs'... not found
Checking `sniffer'...   eth0 is not promisc
Checking `wted'... 8 deletion(s) between Mon Apr 18 06:57:19 2005 and Sat May  4 09:12:17 2024
2 deletion(s) between Mon Apr 18 07:07:31 2005 and Sat May  8 08:38:55 1999
6 deletion(s) between Sun Aug 20 09:10:13 1995 and Wed May 17 19:42:28 2023
nothing deleted
Checking `z2'...
nothing deleted

---

### Post by astoltz on 2005-04-25
Did a quick google and found the following from [linux questions](http://www.linuxquestions.org/questions/archive/4/2004/11/4/259334) 
> 
This is usually an indication that someone has attempted to edit the system logs to hide their accessing the system. Often a sign of security compromise (gain access then hose logs after rooting/backdooring), though having log corruption can cause a false positive. The fact that the date is about 20 years from now usually suggests that's the case. Post the output of last -aix.
Doesn't quite answer your question but some more searching might add some more clues.

---

### Post by dolson on 2005-04-26
Alright, that makes sense then. I noticed the logs were toasted before I even installed chkrootkit, so I'm guessing it is harmless.

Now the question is, how did my logs get corrupted? I was running into issues while changing hard drives, and I ended up having to power down improperly. However, this hasn't ever been a real issue before.

Is it possible that my hard drive is dying? It's fairly new, WD 80GB... I was using a Maxtor 40GB prior to the swap.

Anyhow, here's the log that I noticed was corrupted:

dana     pts/0        63.162.2.200     Mon Apr 25 11:56 - 13:32  (01:35)    
dana     pts/0        63.162.2.200     Tue Apr 19 10:50 - 16:02  (05:11)    
dana     pts/0        63.162.2.200     Tue Apr 19 10:49 - 10:50  (00:00)    
dana     pts/0        63.162.2.200     Tue Apr 19 10:33 - 10:49  (00:15)    
dana     pts/0        63.162.2.200     Tue Apr 19 10:10 - 10:33  (00:23)    
dana     pts/0        63.162.2.200     Mon Apr 18 08:00 - 10:10 (1+02:09)   
dana     pts/0        63.162.2.200     Mon Apr 18 07:51 - 07:56  (00:04)    
dana     pts/1        digory.narnia.la Mon Apr 18 07:15 - 02:55 (1+19:40)   
reboot   system boot  2.4.30           Mon Apr 18 07:13         (7+17:52)   
ddff84
c 2083216
c018 _facf8d2f
c01824 Thu Sep 14 22:18 - crash (-8550+-15:-
edad3e
c f069bfc3
c01 Rsmp_8c590f4d
c0 Fri Nov 14 03:52 - crash (-9705+-21:-
_buffer_ ntry_Rsmp_b3 f88c fat_notify_ Wed Apr 17 17:00 - crash (-6939+-9:-4
eb34a
c0 
c016e914 jo ee_buffers_Rsmp_ Tue Oct 12 19:54 - crash (-6021+-12:-
ke
c0264 _down_write_ cesize_Rsmp_ce5a Sun Aug 20 09:10 - crash (3528+22:03)
01b5
c02 0d93
c0315a4 d36f
c0262860 ge Fri Jun 11 15:40 - crash (2137+15:32)
6ef39
c0 0 nf_registe ue_handler_Rsmp_ Thu Oct 17 01:15 - crash (-3103+-18:-
21adc8 q qdisc_new_es _9c9ef4c2
c021af Sat May  8 08:38 - crash (2171+22:34)
dana     tty2                          Mon Apr 18 07:06 - down   (00:01)    
root     tty1                          Mon Apr 18 07:01 - down   (00:06)    
reboot   system boot  2.4.30           Mon Apr 18 06:59          (00:07)    
c set_bu  balance_dir da86
c013d070 ge Sat Aug 19 00:14 - crash (3530+06:45)
c060
c03 a20170
c0108 
c0128348 get_us Thu Sep 12 12:02 - crash (3139+18:56)
mp_3889b 9ad224b
c011 Rsmp_f0a529b7
c0 Tue Jul  1 19:04 - crash (-7379+-12:-
Rsmp_85d trspn_Rsmp_c Rsmp_a34f1ef5
c0 Tue Nov 18 16:32 - crash (-9710+-10:-
_Rsmp_47 7606a04f
c01 uid_Rsmp_8b618d0 Fri Apr 25 18:55 - crash (2914+12:04)
0 read_a _special_ino 83c get_hash_tab Sun Sep  8 16:45 - crash (3143+14:14)
execve_R gs_kernel_Rs ush_old_exec_Rsm Mon Mar 21 03:20 - crash (-6180+-21:-
0cbf8a9
 _9a3de8f8
c0 _5b4eb2e4
c0154b Mon Mar 17 00:06 - crash (-9463+-18:-
ne_halt_ restart_Rsmp achine_power_off Mon Oct 11 07:29 - crash (-6020+00:-3
Rsmp_9ae intf_Rsmp_84 Rsmp_c258c906
c0 Fri Dec 24 22:17 - crash (1941+07:42)
a460 kst 8 loops_per_ 0 nr_running_Rsm Sat Sep  4 22:49 - crash (-5983+-15:-
n_timeou 3e4cb
c0117c  schedule_Rsmp_4 Mon Apr 28 19:18 - crash (2911+11:41)
49501d4
 dab
c011f858 _Rsmp_865ebccd
c Sat Oct 12 06:18 - crash (3110+00:41)
72b243d4 smp_43435480 Rsmp_375c41f8
c0 Fri Sep 25 18:30 - crash (-5639+-11:-
4c8 allo _br_write_un 0152544 free_kio Sat Sep 19 17:17 - crash (-5633+-10:-
_b121390 _136eba7c
c0 _Rsmp_ab600421
c Sat Aug 27 14:24 - crash (-6340+-7:-2
add_time ngvec_minmax  del_timer_Rsmp_ Sat Nov  2 21:28 - crash (-9329+-15:-
20be8 sy ister_sysctl f
c0120d14 sysct Tue Sep 29 13:22 - crash (-5643+-6:-2
t_Rsmp_4 put_Rsmp_690 r_binfmt_Rsmp_7e Thu Dec  7 14:42 - crash (-6807+-8:-4
_sent_Rs smp_ae4a882b _check_change_Rs Sun Jul 13 04:00 - crash (10872+02:59
f60d
c01 3bd545
c0141 18b7c7
c01417a4  Thu Jan  6 21:47 - crash (-8298+-15:-
4
c034b2 03365a0 tty_ 0b4b6
c034b640 h Sat Jan 24 02:18 - crash (-7585+-20:-
k_page_R fdatawait_Rs lock_page_Rsmp_b Sun Oct 25 09:31 - crash (2366+20:28)
_dir_fsy _lseek_Rsmp_ 4 dcache_readdir Wed Apr 17 20:03 - crash (-6939+-13:-
ode_oper mp_792b3b7f
 3ec18 block_syml Thu Nov  3 15:11 - crash (-6408+-9:-1
c012be68 d4c find_try p_241cfffb
c012b Tue Oct 12 07:32 - crash (-6021+00:-3
p_433f63 smp_d3d28dd2 smp_4936673a
c01 Mon Apr 25 01:31 - crash (-6215+-18:-
umber_Rs _Rsmp_4885e1 subdir_Rsmp_916c Sat May  4 09:12 - crash (-6956+-2:-1
reboot   system boot  2.4.30           Mon Apr 18 06:56          (00:10)    
dana     tty1                          Mon Apr 18 06:50 - down   (00:01)    
reboot   system boot  2.4.30           Mon Apr 18 06:50          (00:02)    
dana     pts/1        digory.narnia.la Mon Apr 18 02:40 - crash  (04:09)    
reboot   system boot  2.4.26           Mon Apr 18 02:38          (04:14)    
dana     pts/2        polly.narnia.lan Sun Apr 17 23:48 - 23:48  (00:00)    
dana     pts/2        63.162.2.200     Fri Apr 15 14:01 - 16:48  (02:46)    
dana     pts/2        63.162.2.200     Fri Apr 15 08:24 - 12:33  (04:09)    
dana     pts/2        polly.narnia.lan Thu Apr 14 20:18 - 08:24  (12:06)    
dana     pts/2        63.162.2.200     Thu Apr 14 11:19 - 11:20  (00:01)    
dana     pts/2        63.162.2.200     Thu Apr 14 08:07 - 08:08  (00:00)    
iphitus  ftpd11372    210.49.173.87    Wed Apr 13 09:54 - 10:00  (00:06)    
dana     ftpd10088    polly.narnia.lan Wed Apr 13 00:40 - 00:50  (00:10)    
dana     ftpd10080    polly.narnia.lan Wed Apr 13 00:36 - 00:40  (00:04)    
dana     ftpd10079    polly.narnia.lan Wed Apr 13 00:36 - 00:36  (00:00)    
dana     ftpd10076    polly.narnia.lan Wed Apr 13 00:36 - 00:36  (00:00)    
dana     ftpd10072    polly.narnia.lan Wed Apr 13 00:36 - 00:36  (00:00)    
dana     pts/2        polly.narnia.lan Wed Apr 13 00:36 - 00:36  (00:00)    
dana     ftpd10051    polly.narnia.lan Wed Apr 13 00:36 - 00:36  (00:00)    
dana     ftpd10048    polly.narnia.lan Wed Apr 13 00:35 - 00:36  (00:00)    
dana     ftpd10047    polly.narnia.lan Wed Apr 13 00:35 - 00:35  (00:00)    
dana     ftpd10046    polly.narnia.lan Wed Apr 13 00:35 - 00:35  (00:00)    
dana     ftpd10045    polly.narnia.lan Wed Apr 13 00:35 - 00:35  (00:00)    
dana     ftpd10041    polly.narnia.lan Wed Apr 13 00:34 - 00:35  (00:00)    
dana     ftpd10040    polly.narnia.lan Wed Apr 13 00:34 - 00:35  (00:00)    
dana     ftpd10039    polly.narnia.lan Wed Apr 13 00:33 - 00:43  (00:10)    
dana     pts/2        63.162.2.200     Tue Apr 12 10:35 - 10:44  (00:09)    
dana     pts/6        digory.narnia.la Mon Apr 11 06:17 - 06:20  (00:02)    
iphitus  pts/6        210.49.173.87    Sun Apr 10 22:36 - 22:37  (00:00)    
iphitus  pts/6        210.49.173.87    Sun Apr 10 22:26 - 22:30  (00:04)    
dana     pts/6        digory.narnia.la Sun Apr 10 02:58 - 03:16  (00:17)    
dana     pts/6        digory.narnia.la Sat Apr  9 17:57 - 02:58  (09:00)    
dana     pts/6        polly.narnia.lan Fri Apr  8 23:06 - 01:20  (02:14)    
dana     pts/2        63.162.2.200     Fri Apr  8 19:26 - 10:16 (3+14:49)   
dana     pts/2        63.162.2.200     Fri Apr  8 11:07 - 11:28  (00:21)    
iphitus  pts/2        210.49.173.87    Fri Apr  8 06:43 - 07:14  (00:30)    
dana     ftpd20204    digory.narnia.la Fri Apr  8 04:00 - 04:10  (00:10)    
dana     ftpd20184    digory.narnia.la Fri Apr  8 03:59 - 04:01  (00:02)    
dana     ftpd20182    digory.narnia.la Fri Apr  8 03:55 - 03:59  (00:04)    
dana     ftpd20181    digory.narnia.la Fri Apr  8 03:55 - 04:01  (00:06)    
dana     ftpd20180    digory.narnia.la Fri Apr  8 03:55 - 03:55  (00:00)    
dana     ftpd20176    digory.narnia.la Fri Apr  8 03:54 - 03:55  (00:00)    
dana     ftpd20171    digory.narnia.la Fri Apr  8 03:50 - 03:55  (00:04)    
dana     ftpd20165    digory.narnia.la Fri Apr  8 03:48 - 03:50  (00:02)    
dana     ftpd20164    digory.narnia.la Fri Apr  8 03:48 - 03:59  (00:11)    
dana     ftpd20163    digory.narnia.la Fri Apr  8 03:46 - 03:54  (00:08)    
dana     ftpd20162    digory.narnia.la Fri Apr  8 03:46 - 03:48  (00:01)    
dana     ftpd20161    digory.narnia.la Fri Apr  8 03:46 - 03:46  (00:00)    
dana     ftpd20160    digory.narnia.la Fri Apr  8 03:45 - 03:46  (00:01)    
dana     ftpd20156    digory.narnia.la Fri Apr  8 03:44 - 03:45  (00:01)    
dana     ftpd20155    digory.narnia.la Fri Apr  8 03:44 - 03:46  (00:01)    
dana     ftpd20154    digory.narnia.la Fri Apr  8 03:42 - 03:44  (00:01)    
dana     ftpd20153    digory.narnia.la Fri Apr  8 03:42 - 03:42  (00:00)    
dana     ftpd20152    digory.narnia.la Fri Apr  8 03:42 - 03:42  (00:00)    
dana     ftpd20151    digory.narnia.la Fri Apr  8 03:41 - 03:42  (00:00)    
dana     ftpd20149    digory.narnia.la Fri Apr  8 03:40 - 03:41  (00:00)    
dana     ftpd20148    digory.narnia.la Fri Apr  8 03:40 - 03:42  (00:01)    
dana     ftpd20147    digory.narnia.la Fri Apr  8 03:40 - 03:56  (00:16)    
dana     pts/6        digory.narnia.la Fri Apr  8 03:26 - 03:30  (00:04)    
dana     pts/2        digory.narnia.la Fri Apr  8 03:20 - 03:32  (00:11)    
dana     pts/2        polly.narnia.lan Fri Apr  8 00:41 - 03:20  (02:38)    
dana     ftpd19709    polly.narnia.lan Fri Apr  8 00:18 - 00:29  (00:10)    
dana     ftpd19708    polly.narnia.lan Fri Apr  8 00:18 - 00:18  (00:00)    
dana     ftpd19707    polly.narnia.lan Fri Apr  8 00:18 - 00:18  (00:00)    
dana     ftpd19706    polly.narnia.lan Fri Apr  8 00:18 - 00:18  (00:00)    
iphitus  pts/2        210.49.173.87    Wed Apr  6 19:32 - 21:58  (02:26)    
dana     pts/2        63.162.2.200     Tue Apr  5 09:52 - 10:22  (00:30)    
dana     pts/7        63.162.2.200     Mon Apr  4 10:08 - 11:33  (01:25)    
dropbox  ftpd1492     router.narnia.la Sun Apr  3 16:33 - 16:38  (00:05)    
dropbox  ftpd1491     router.narnia.la Sun Apr  3 16:33 - 16:33  (00:00)    
dropbox  ftpd1490     router.narnia.la Sun Apr  3 16:31 - 16:33  (00:02)    
dana     pts/7        digory.narnia.la Sun Apr  3 16:10 - 16:59  (00:48)    
dropbox  ftpd32655    24.43.132.168    Sun Apr  3 11:03 - 11:09  (00:06)    
dana     pts/7        digory.narnia.la Sat Apr  2 14:31 - 14:34  (00:02)    
dana     pts/7        digory.narnia.la Sat Apr  2 13:21 - 13:43  (00:21)    
iphitus  pts/7        210.49.173.87    Sat Apr  2 10:50 - 10:51  (00:01)    
dana     ftpd27661    digory.narnia.la Sat Apr  2 04:59 - 04:59  (00:00)    
dana     ftpd27660    digory.narnia.la Sat Apr  2 04:59 - 04:59  (00:00)    
dana     ftpd27659    digory.narnia.la Sat Apr  2 04:59 - 05:09  (00:10)    
dana     ftpd27658    digory.narnia.la Sat Apr  2 04:57 - 04:58  (00:00)    
dana     ftpd27657    digory.narnia.la Sat Apr  2 04:57 - 04:57  (00:00)    
dana     pts/7        digory.narnia.la Sat Apr  2 01:16 - 01:44  (00:27)    
dana     pts/7        63.162.2.200     Fri Apr  1 14:29 - 15:26  (00:56)    
dana     pts/7        63.162.2.200     Fri Apr  1 12:47 - 14:29  (01:41)

---

