---
title: "Assign ftp name to ip address on local network?"
date: 2008-05-26
forum: General Help
---

### Post by sdowney717 on 2008-05-26
I can type [ftp://192.168.1.100](ftp://192.168.1.100) and see my file list in firefox

How could I simply type in something like ftp.scottdesktop.com and have it bring up the file list?

I am using vsftpd as my ftp server.

---

### Post by Grognot on 2008-05-26
Easiest way would simply be to add the hostname to your hosts files

---

### Post by blom on 2008-05-26
That'll work as long as the address doesn't change (DHCP etc.) or you don't mind changing the hosts file if it does.

Maybe your (ADSL?) router supports dynamic DNS and is your DHCP server - I know that some of them do... worth a look, but Grognot's answer maybe all you need

---

### Post by sdowney717 on 2008-05-26
thanks, where is the hosts file?

this is in my /etc/hosts file

127.0.0.1	localhost
127.0.1.1	scott-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by joberly on 2008-05-26
Yup, just add a line for the machine you want FTP access to.

example:

192.168.1.101 ftpmachine

Then you can [ftp://ftpmachine](ftp://ftpmachine)

Change ftpmachine to whatever pseudonym you want.

You can only edit the hosts file with root access, so you can do something like:

sudo gedit /etc/hosts

---

### Post by sdowney717 on 2008-05-26
that does work.
I am trying to upgrade a firmware for a dlink dsm320 and I can enter the ftp server name on the dsm320 but it wont connect. The dsm320 does connect to the internet, so at least that works.

the FTP upgrade link used to be ftp.dlink.com/medialounge/DSM320

But if I type in [ftp://ftpmachine](ftp://ftpmachine) into the dsm320 ftp upgrade server link setting, , that DSM320 box cant find it.
So I was wondering if it has to be something like ftp.mymachinename.com in order for it to work?
any ideas?
It is a complicated mess, they dont support it properly anymore so when it would go to their website, it never could find the proper firmware. 
I found out several manual methods to try so I am trying. So I was wondering if it has to match their ftp.***.com idea to work.

It follows this idea based on this webpost
[http://p214.ezboard.com/fdsm320frm2.showMessageRange?topicID=83.topic&start=21&stop=35](http://p214.ezboard.com/fdsm320frm2.showMessageRange?topicID=83.topic&start=21&stop=35)

---

### Post by joberly on 2008-05-26
I'm assuming the DSM320 will download automatically from the DLink upgrade server right? And it lets you change the address of the upgrade server?

You said the upgrade address used to be ftp.dlink.com/Medialounge/DSM320? I don't see why that link wouldn't work, as I just visited that location and the files seem to be there.

---

### Post by sdowney717 on 2008-05-26
yes I know what your saying!
Yes, I can chane the address location of where the dsm320 will look for the files.

The little I have gleaned is that the file dsm320-versioninfo.txt is a problem.
The first line of the file states your current version on your dsm320
The second line states the firmware file name to upgrade to

so the file on their server says
VERSION='1.03ww'
LOCATION='FW-1.03ww'

and it should be for my situation
VERSION='1.05'
LOCATION='FW-1.09'

And It sort of makes no sense to me why the programmers would do this since every machine could have differing firmware versions. But if you follow the mans post on the other forum you will see what I mean.

The other possibility is to telnet into the device which I have done. 
And upgrade but there is a problem with getting the file over to it.
There is no space on the ram for the firmware? and somehow it would have to be linked?

[http://dsm320.yuku.com/topic/393/t/Telnet-access-to-the-DSM320RD-and-what-to-do-with-it.html](http://dsm320.yuku.com/topic/393/t/Telnet-access-to-the-DSM320RD-and-what-to-do-with-it.html)

This is what I did and what the problem is
[http://ubuntuforums.org/showthread.php?t=801615](http://ubuntuforums.org/showthread.php?t=801615)

---

### Post by joberly on 2008-05-26
Are you logged into the DSM as root or an administrative login? Once you telnet in, do an fdisk -l and it will list what devices are attached. Just because Ubuntu sees it as sdc1, doesn't necessarily mean the DSM will. Fdisk -l will give you the list, then mount the appropriate drive.

The mount command only gives you what is currently mounted, where fdisk will give you a list of attached devices.

Mount your memory stick, and then run the ./update_firm -f "/wherever_you_mounted_the_memory_stick/firmware_file


See if that works.

Seems like it may be easier to burn the cd with the firmware on it, because the DSM auto-mounts the DVD drive when a cd is inserted, correct?

---

### Post by sdowney717 on 2008-05-26
telnet in but fdisk not working
mount shows some info

also, I dont fully understand his post
wonder what the 'wait till dsm sees file means'
does this mean it somehow shows up in dsm file directory?

-Changing Firmware-
Now that you have telnet access, you can either load a CD or a memory card with the firmware you want. The following steps are for a CD, but for a memory card just replace "/tmp/dvd" with "/tmp/usbmount_ready". Between ' are the commands you should type.

- do a 'telnet "dsm-ip-address"' - you should get a command prompt;
- load the CD with the firmware file (FW-RD-1.01eu or another);
- wait until the DSM shows the CD as loaded, then do a 'ls -l /tmp/dvd' and make sure you can see the "FW-RD-1.01eu" file in the resulting list;
- 'cd /sbin'
- './update_firm -f "/tmp/dvd/FW-RD-1.01eu"'
- wait for the input prompt to show again (it should take 5 minutes or so);
- 'reboot'
- turn the DSM on again;
- remove the CD;
- press 'setup', choose 'system->reset to factory defaults'

Your "new" firmware should now be ready.

```

scott@scott-desktop:~$ sudo telnet 192.168.1.104
Trying 192.168.1.104...
Connected to 192.168.1.104.
Escape character is '^]'.



BusyBox v0.60.1 (2005.02.06-02:08+0000) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

# ls -l
lrwxrwxrwx    1 0        0              26 audio_browse.xml -> /tmp//osd/audio_browse.xml
lrwxrwxrwx    1 0        0              22 keyboard.xml -> /tmp//osd/keyboard.xml
drwxr-xr-x    1 0        0            6608 image
-rw-r--r--    1 0        0             887 privkeyCln.pem
-rw-r--r--    1 0        0            3005 certCln.pem
-rw-r--r--    1 0        0             989 CAcertSrv.pem
-rw-r--r--    1 0        0             164 setup_menu.xml
lrwxrwxrwx    1 0        0              24 aol2_snpwd.xml -> /tmp//osd/aol2_snpwd.xml
-rw-r--r--    1 0        0             290 aol2showtext.xml
lrwxrwxrwx    1 0        0              28 aol2showmsgbox.xml -> /tmp//osd/aol2showmsgbox.xml
lrwxrwxrwx    1 0        0              35 aol2setup_ygpsettings.xml -> /tmp//osd/aol2setup_ygpsettings.xml
lrwxrwxrwx    1 0        0              32 aol2setup_srvsetup.xml -> /tmp//osd/aol2setup_srvsetup.xml
lrwxrwxrwx    1 0        0              37 aol2setup_srvconn_setup.xml -> /tmp//osd/aol2setup_srvconn_setup.xml
lrwxrwxrwx    1 0        0              29 aol2setup_snpwd.xml -> /tmp//osd/aol2setup_snpwd.xml
lrwxrwxrwx    1 0        0              33 aol2setup_rmconfirm.xml -> /tmp//osd/aol2setup_rmconfirm.xml
lrwxrwxrwx    1 0        0              39 aol2setup_only_registered.xml -> /tmp//osd/aol2setup_only_registered.xml
lrwxrwxrwx    1 0        0              26 aol2services.xml -> /tmp//osd/aol2services.xml
lrwxrwxrwx    1 0        0              29 aol2r_trial_tos.xml -> /tmp//osd/aol2r_trial_tos.xml
lrwxrwxrwx    1 0        0              33 aol2r_trial_details.xml -> /tmp//osd/aol2r_trial_details.xml
lrwxrwxrwx    1 0        0              33 aol2r_srvconn_setup.xml -> /tmp//osd/aol2r_srvconn_setup.xml
lrwxrwxrwx    1 0        0              23 aol2radio.xml -> /tmp//osd/aol2radio.xml
lrwxrwxrwx    1 0        0              34 aol2radio-presetmenu.xml -> /tmp//osd/aol2radio-presetmenu.xml
lrwxrwxrwx    1 0        0              32 aol2r_access_radio.xml -> /tmp//osd/aol2r_access_radio.xml
lrwxrwxrwx    1 0        0              23 aol2p_tos.xml -> /tmp//osd/aol2p_tos.xml
lrwxrwxrwx    1 0        0              29 aol2p_subscribe.xml -> /tmp//osd/aol2p_subscribe.xml
lrwxrwxrwx    1 0        0              24 aol2preset.xml -> /tmp//osd/aol2preset.xml
lrwxrwxrwx    1 0        0              29 aol2p_nonmember.xml -> /tmp//osd/aol2p_nonmember.xml
lrwxrwxrwx    1 0        0              23 aol2photo.xml -> /tmp//osd/aol2photo.xml
lrwxrwxrwx    1 0        0              28 aol2photo-play.xml -> /tmp//osd/aol2photo-play.xml
lrwxrwxrwx    1 0        0              33 aol2photo-play-menu.xml -> /tmp//osd/aol2photo-play-menu.xml
lrwxrwxrwx    1 0        0              34 aol2photo-notify-aol.xml -> /tmp//osd/aol2photo-notify-aol.xml
lrwxrwxrwx    1 0        0              34 aol2photo-image-info.xml -> /tmp//osd/aol2photo-image-info.xml
lrwxrwxrwx    1 0        0              30 aol2photo-folder.xml -> /tmp//osd/aol2photo-folder.xml
lrwxrwxrwx    1 0        0              35 aol2photo-folder-menu.xml -> /tmp//osd/aol2photo-folder-menu.xml
lrwxrwxrwx    1 0        0              36 aol2photo-delete-image.xml -> /tmp//osd/aol2photo-delete-image.xml
lrwxrwxrwx    1 0        0              36 aol2photo-delete-album.xml -> /tmp//osd/aol2photo-delete-album.xml
lrwxrwxrwx    1 0        0              29 aol2photo-album.xml -> /tmp//osd/aol2photo-album.xml
lrwxrwxrwx    1 0        0              34 aol2photo-album-play.xml -> /tmp//osd/aol2photo-album-play.xml
lrwxrwxrwx    1 0        0              34 aol2photo-album-info.xml -> /tmp//osd/aol2photo-album-info.xml
-rw-r--r--    1 0        0             728 aol2only_member.xml
lrwxrwxrwx    1 0        0              24 aol2msgbox.xml -> /tmp//osd/aol2msgbox.xml
lrwxrwxrwx    1 0        0              25 aol2msgbox2.xml -> /tmp//osd/aol2msgbox2.xml
-rw-r--r--    1 0        0             819 aol2invalid_snpwd.xml
-rw-r--r--    1 0        0             746 copy_data.xml
lrwxrwxrwx    1 0        0              33 live365_stationlist.xml -> /tmp//osd/live365_stationlist.xml
lrwxrwxrwx    1 0        0              28 live365_signup.xml -> /tmp//osd/live365_signup.xml
lrwxrwxrwx    1 0        0              31 live365_setuphome.xml -> /tmp//osd/live365_setuphome.xml
lrwxrwxrwx    1 0        0              27 live365_setup.xml -> /tmp//osd/live365_setup.xml
lrwxrwxrwx    1 0        0              28 live365_search.xml -> /tmp//osd/live365_search.xml
lrwxrwxrwx    1 0        0              29 live365_preopen.xml -> /tmp//osd/live365_preopen.xml
lrwxrwxrwx    1 0        0              26 live365_play.xml -> /tmp//osd/live365_play.xml
lrwxrwxrwx    1 0        0              26 live365_home.xml -> /tmp//osd/live365_home.xml
lrwxrwxrwx    1 0        0              31 live365_genrelist.xml -> /tmp//osd/live365_genrelist.xml
-rw-r--r--    1 0        0             879 copy.xml
lrwxrwxrwx    1 0        0              33 wizard_wirelessdata.xml -> /tmp//osd/wizard_wirelessdata.xml
lrwxrwxrwx    1 0        0              27 wizard_wepkey.xml -> /tmp//osd/wizard_wepkey.xml
lrwxrwxrwx    1 0        0              28 wizard_welcome.xml -> /tmp//osd/wizard_welcome.xml
lrwxrwxrwx    1 0        0              27 wizard_survey.xml -> /tmp//osd/wizard_survey.xml
lrwxrwxrwx    1 0        0              27 wizard_setdns.xml -> /tmp//osd/wizard_setdns.xml
lrwxrwxrwx    1 0        0              28 wizard_servers.xml -> /tmp//osd/wizard_servers.xml
lrwxrwxrwx    1 0        0              28 wizard_network.xml -> /tmp//osd/wizard_network.xml
lrwxrwxrwx    1 0        0              28 wizard_lantype.xml -> /tmp//osd/wizard_lantype.xml
lrwxrwxrwx    1 0        0              27 wizard_iptype.xml -> /tmp//osd/wizard_iptype.xml
lrwxrwxrwx    1 0        0              39 wizard_incompletedmessage.xml -> /tmp//osd/wizard_incompletedmessage.xml
lrwxrwxrwx    1 0        0              29 wizard_firmware.xml -> /tmp//osd/wizard_firmware.xml
lrwxrwxrwx    1 0        0              28 wizard_dnstype.xml -> /tmp//osd/wizard_dnstype.xml
lrwxrwxrwx    1 0        0              27 wizard_device.xml -> /tmp//osd/wizard_device.xml
lrwxrwxrwx    1 0        0              37 wizard_completedmessage.xml -> /tmp//osd/wizard_completedmessage.xml
-rw-r--r--    1 0        0            2635 video_seektime_input.xml
lrwxrwxrwx    1 0        0              23 video_run.xml -> /tmp//osd/video_run.xml
lrwxrwxrwx    1 0        0              27 video_preopen.xml -> /tmp//osd/video_preopen.xml
lrwxrwxrwx    1 0        0              26 video_browse.xml -> /tmp//osd/video_browse.xml
lrwxrwxrwx    1 0        0              23 setup_ftp.xml -> /tmp//osd/setup_ftp.xml
lrwxrwxrwx    1 0        0              26 view_servers.xml -> /tmp//osd/view_servers.xml
lrwxrwxrwx    1 0        0              39 setup_wireless_sitesurvey.xml -> /tmp//osd/setup_wireless_sitesurvey.xml
lrwxrwxrwx    1 0        0              28 setup_wireless.xml -> /tmp//osd/setup_wireless.xml
lrwxrwxrwx    1 0        0              27 setup_version.xml -> /tmp//osd/setup_version.xml
lrwxrwxrwx    1 0        0              26 setup_system.xml -> /tmp//osd/setup_system.xml
lrwxrwxrwx    1 0        0              28 setup_network2.xml -> /tmp//osd/setup_network2.xml
lrwxrwxrwx    1 0        0              27 setup_network.xml -> /tmp//osd/setup_network.xml
-rw-r--r--    1 0        0            4137 setup_misc_tv_trick.xml
lrwxrwxrwx    1 0        0              27 setup_misc_tv.xml -> /tmp//osd/setup_misc_tv.xml
-rw-r--r--    1 0        0            1238 setup_misc_ping.xml
lrwxrwxrwx    1 0        0              33 setup_misc_parental.xml -> /tmp//osd/setup_misc_parental.xml
lrwxrwxrwx    1 0        0              30 setup_misc_music.xml -> /tmp//osd/setup_misc_music.xml
lrwxrwxrwx    1 0        0              33 setup_misc_language.xml -> /tmp//osd/setup_misc_language.xml
lrwxrwxrwx    1 0        0              32 setup_misc_general.xml -> /tmp//osd/setup_misc_general.xml
lrwxrwxrwx    1 0        0              24 setup_misc.xml -> /tmp//osd/setup_misc.xml
lrwxrwxrwx    1 0        0              31 setup_menu_DSM320.xml -> /tmp//osd/setup_menu_DSM320.xml
-rw-r--r--    1 0        0            1889 setup_memorycard.xml
lrwxrwxrwx    1 0        0              26 setup_locale.xml -> /tmp//osd/setup_locale.xml
lrwxrwxrwx    1 0        0              30 setup_dvd_region.xml -> /tmp//osd/setup_dvd_region.xml
lrwxrwxrwx    1 0        0              27 preset_browse.xml -> /tmp//osd/preset_browse.xml
lrwxrwxrwx    1 0        0              27 search_result.xml -> /tmp//osd/search_result.xml
lrwxrwxrwx    1 0        0              20 search.xml -> /tmp//osd/search.xml
lrwxrwxrwx    1 0        0              25 select_menu.xml -> /tmp//osd/select_menu.xml
lrwxrwxrwx    1 0        0              34 rename_playlist_item.xml -> /tmp//osd/rename_playlist_item.xml
lrwxrwxrwx    1 0        0              29 rename_playlist.xml -> /tmp//osd/rename_playlist.xml
lrwxrwxrwx    1 0        0              27 playlist_menu.xml -> /tmp//osd/playlist_menu.xml
lrwxrwxrwx    1 0        0              32 playlist_item_menu.xml -> /tmp//osd/playlist_item_menu.xml
lrwxrwxrwx    1 0        0              34 playlist_item_browse.xml -> /tmp//osd/playlist_item_browse.xml
lrwxrwxrwx    1 0        0              34 playlist_edit_browse.xml -> /tmp//osd/playlist_edit_browse.xml
lrwxrwxrwx    1 0        0              29 playlist_browse.xml -> /tmp//osd/playlist_browse.xml
lrwxrwxrwx    1 0        0              26 new_playlist.xml -> /tmp//osd/new_playlist.xml
lrwxrwxrwx    1 0        0              36 rename_photoalbum_item.xml -> /tmp//osd/rename_photoalbum_item.xml
lrwxrwxrwx    1 0        0              31 rename_photoalbum.xml -> /tmp//osd/rename_photoalbum.xml
lrwxrwxrwx    1 0        0              29 photoalbum_menu.xml -> /tmp//osd/photoalbum_menu.xml
lrwxrwxrwx    1 0        0              34 photoalbum_item_menu.xml -> /tmp//osd/photoalbum_item_menu.xml
lrwxrwxrwx    1 0        0              31 photoalbum_browse.xml -> /tmp//osd/photoalbum_browse.xml
lrwxrwxrwx    1 0        0              28 new_photoalbum.xml -> /tmp//osd/new_photoalbum.xml
-rw-r--r--    1 0        0             732 picture_view_menu_zoom.xml
-rw-r--r--    1 0        0             946 picture_view_menu_rotate.xml
lrwxrwxrwx    1 0        0              31 picture_view_menu.xml -> /tmp//osd/picture_view_menu.xml
lrwxrwxrwx    1 0        0              25 picture_run.xml -> /tmp//osd/picture_run.xml
lrwxrwxrwx    1 0        0              29 picture_preopen.xml -> /tmp//osd/picture_preopen.xml
lrwxrwxrwx    1 0        0              33 picture_list_browse.xml -> /tmp//osd/picture_list_browse.xml
lrwxrwxrwx    1 0        0              28 picture_browse.xml -> /tmp//osd/picture_browse.xml
-rw-r--r--    1 0        0             941 napster_info_pg2.xml
-rw-r--r--    1 0        0            1044 napster_info_pg1.xml
lrwxrwxrwx    1 0        0              26 rhap_playing.xml -> /tmp//osd/rhap_playing.xml
lrwxrwxrwx    1 0        0              25 rhap_browse.xml -> /tmp//osd/rhap_browse.xml
lrwxrwxrwx    1 0        0              42 online_home_DSM320_with_RHAP.xml -> /tmp//osd/online_home_DSM320_with_RHAP.xml
-rw-r--r--    1 0        0            1599 online_home_DSM320_Napster.xml
-rw-r--r--    1 0        0            1332 online_home_DSM320RH.xml
lrwxrwxrwx    1 0        0              32 online_home_DSM320.xml -> /tmp//osd/online_home_DSM320.xml
lrwxrwxrwx    1 0        0              23 passwdbox.xml -> /tmp//osd/passwdbox.xml
lrwxrwxrwx    1 0        0              20 update.xml -> /tmp//osd/update.xml
lrwxrwxrwx    1 0        0              19 blank.xml -> /tmp//osd/blank.xml
lrwxrwxrwx    1 0        0              23 audio_run.xml -> /tmp//osd/audio_run.xml
lrwxrwxrwx    1 0        0              27 audio_preopen.xml -> /tmp//osd/audio_preopen.xml
lrwxrwxrwx    1 0        0              33 audio_browse_DSM320.xml -> /tmp//osd/audio_browse_DSM320.xml
lrwxrwxrwx    1 0        0              22 wmc_auth.xml -> /tmp//osd/wmc_auth.xml
lrwxrwxrwx    1 0        0              30 wizard_ok_msgbox.xml -> /tmp//osd/wizard_ok_msgbox.xml
lrwxrwxrwx    1 0        0              37 wizard_ok_cancel_msgbox.xml -> /tmp//osd/wizard_ok_cancel_msgbox.xml
lrwxrwxrwx    1 0        0              27 wizard_msgbox.xml -> /tmp//osd/wizard_msgbox.xml
lrwxrwxrwx    1 0        0              34 wizard_cancel_msgbox.xml -> /tmp//osd/wizard_cancel_msgbox.xml
lrwxrwxrwx    1 0        0              21 welcome.xml -> /tmp//osd/welcome.xml
lrwxrwxrwx    1 0        0              27 update_msgbox.xml -> /tmp//osd/update_msgbox.xml
lrwxrwxrwx    1 0        0              29 stop_background.xml -> /tmp//osd/stop_background.xml
lrwxrwxrwx    1 0        0              20 server.xml -> /tmp//osd/server.xml
lrwxrwxrwx    1 0        0              25 screensaver.xml -> /tmp//osd/screensaver.xml
lrwxrwxrwx    1 0        0              25 rhap_server.xml -> /tmp//osd/rhap_server.xml
lrwxrwxrwx    1 0        0              25 rhap_msgbox.xml -> /tmp//osd/rhap_msgbox.xml
-rw-r--r--    1 0        0              40 poweroff.xml
lrwxrwxrwx    1 0        0              21 popmenu.xml -> /tmp//osd/popmenu.xml
lrwxrwxrwx    1 0        0              24 old-msgbox.xml -> /tmp//osd/old-msgbox.xml
lrwxrwxrwx    1 0        0              29 ok_title_msgbox.xml -> /tmp//osd/ok_title_msgbox.xml
lrwxrwxrwx    1 0        0              23 ok_msgbox.xml -> /tmp//osd/ok_msgbox.xml
lrwxrwxrwx    1 0        0              30 ok_cancel_msgbox.xml -> /tmp//osd/ok_cancel_msgbox.xml
lrwxrwxrwx    1 0        0              20 msgbox.xml -> /tmp//osd/msgbox.xml
lrwxrwxrwx    1 0        0              26 keypad_upper.xml -> /tmp//osd/keypad_upper.xml
lrwxrwxrwx    1 0        0              26 keypad_lower.xml -> /tmp//osd/keypad_lower.xml
lrwxrwxrwx    1 0        0              25 home_dsm320.xml -> /tmp//osd/home_dsm320.xml
lrwxrwxrwx    1 0        0              22 dma_home.xml -> /tmp//osd/dma_home.xml
lrwxrwxrwx    1 0        0              27 cancel_msgbox.xml -> /tmp//osd/cancel_msgbox.xml
lrwxrwxrwx    1 0        0              23 basic_run.xml -> /tmp//osd/basic_run.xml
lrwxrwxrwx    1 0        0              27 basic_preopen.xml -> /tmp//osd/basic_preopen.xml
lrwxrwxrwx    1 0        0              26 basic_browse.xml -> /tmp//osd/basic_browse.xml
# cd /tmp
# ls
downloading_firminfo firstrunosd     config          osd             bin             sbin            usr             ramdisk1.gz     dev             lib             conf            dos             var             etc
# cd var
# ls
log             run
# cd ..
# ls
downloading_firminfo firstrunosd     config          osd             bin             sbin            usr             ramdisk1.gz     dev             lib             conf            dos             var             etc
# fdisk
fdisk: No such file or directory
# mount
/dev/ram0 on / type ext2 (rw)
/mtd_rootfs_dev on /mtd_rootfs type cramfs (ro)
none on /proc type proc (rw)
/dev/ram1 on /tmp type ext2 (rw)
# 

```

---

### Post by sdowney717 on 2008-05-26
here is ls /tmp
I dont see the file listed
Also I am running mediatomb and I shared where the firmware is located and I can using the dsm navigation screen, go to that file location showing on the TV.
(you run a uPNP media server that the dsm connects to and you casn see a file directory structure)

# ls -l /tmp 
-rw-r--r--    1 0        0               0 downloading_firminfo
-rw-r--r--    1 0        0               0 firstrunosd
-rw-r--r--    1 0        0             269 config
drwxr-xr-x    3 0        0            4096 osd
drwxr-xr-x    2 0        0            1024 bin
drwxr-xr-x    2 0        0            1024 sbin
drwxr-xr-x    4 0        0            1024 usr
-rw-r--r--    1 0        0            4656 ramdisk1.gz
drwxr-xr-x    2 0        0            1024 dev
drwxr-xr-x    3 0        0            1024 lib
drwxr-xr-x    2 0        0            1024 conf
drwxr-xr-x    2 0        0            1024 dos
drwxr-xr-x    4 0        0            1024 var
drwxr-xr-x    5 0        0            1024 etc

---

### Post by sdowney717 on 2009-11-14
update, this whole issue of firmware updating was resolved by plugging in the DSM 320 directly into the cable modem, bypassing the router

---

