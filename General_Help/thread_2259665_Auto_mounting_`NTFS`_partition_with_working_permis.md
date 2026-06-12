---
title: "Auto mounting `NTFS` partition with working permissions"
date: 2015-01-06
forum: General Help
---

### Post by Vesnog on 2015-01-06
I am mounting a `Windows 7 Home Premium 64-bit` system partition on my `Ubuntu 14.04.1 LTS 64-bit` installation in order to be able to share data between the two OSs. The problem is that although I explicitly give the option *permissions *in **/etc/fstab** file I cannot **chmod **the files or directories inside the mounted drive. I also experimented with it and noticed if I only supplied *permissions *option while mounting(after unmounting everything) it and changed into the mount directory I noticed that everything had **chmod 777** permissions, but I was able to alter the permission via the **chmod **command. The working command is as follows in the command prompt:


    ```
mount -t ntfs-3g -o permissions /dev/sda5 /mnt/DATA/

```

However, I noticed even when I supplied my **uid **and **gid **to own the files the option *permissions *stopped having an effect. I tried appending and prepending it into the list of options just to make sure, and it turned out that in both cases I was not able to alter the permissions with **chmod**. The codes I used in command prompt is as follows:


    ```
sudo mount -t ntfs-3g -o uid=1000,gid=1000,permissions /dev/sda5 /mnt/DATA/

```

After unmounting, one more try as follows:


    ```
sudo mount -t ntfs-3g -o permissions,uid=1000,gid=1000 /dev/sda5 /mnt/DATA/

```

Both of these configurations did not allow me to change the settings and the option **permissions** had literally no effect. In my **/etc/fstab** file I define the line for mounting the **NTFS** partition as follows:


    ```
# data was on /dev/sda5 always
    UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  auto,users,uid=1000,gid=1000,dmask=022,fmask=133,permissions       0       0
```


How can I make **permissions **options work so that I can change the permissions on the go without having to remount the partition totally? I read on [askubuntu ]("http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition")it as possible, but I am unsure of how to do it. I would greatly appreciate any comments suggestions on this issue. My full **/etc/fstab** is as follows:


    ```
# /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/sda6 during installation
    UUID=c6cc14c0-aa75-4660-9e45-10a8fadedb64 /               ext4    errors=remount-ro 0       1
    # /home was on /dev/sda8 during installation
    UUID=30c60dd5-3c79-4e36-8ed7-d8035422f0b6 /home           ext4    defaults        0       2
    # swap was on /dev/sda7 during installation
    UUID=ffbc51d4-25b3-413f-aed1-14eba0f769c7 none            swap    sw              0       0
    # data was on /dev/sda5 always
    UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  auto,users,uid=1000,gid=1000,dmask=022,fmask=133,permissions       0       0
```

Do you suggest any other filesystem to use for sharing data between Windows and Linux? I already asked it on [askubuntu]("http://askubuntu.com/questions/568969/auto-mounting-ntfs-partition-at-startup-not-all-options-work"), but did not get much of a reply.
EDIT: The **DATA** partition is a separate NTFS partition by itself for the sole purpose of file sharing between the two OSs. Windows is installed on another partition.
Thanks in advance

---

### Post by Morbius1 on 2015-01-06
There are a number of issues with the path that you have selected.

***First***, mounting the Windows system partition from Linux as writable is always a dangerous thing to do. It would be better if you created a Windows data partition as ntfs and made that writable.

***Second***, the use of the "permissions" option is not as simple as just adding the option to the mount statement. You need to create what is essentially a conversion table on both Windows and Linux to convert user names from one system to the other. Without that you end up running the risk oh having this happen to you: 
> [http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner](http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner)
OK, I got everything working on the Ubuntu side, with the following options: nls=iso8859-1,permissions,users,auto,exec

However, when I try to access files on the partition from Windows, the security settings are all messed up. On all the files (of those few I've examined) a new account called Account Unknown(long GUID) has been added to the list of users, and has full rights. Rigths for most other users are decreased so that I don't have rights to do stuff I expect. Notably "Everyone" does no longer seem to have right to "Traverse folder / execute".
My advice is just don't dot it. The original proponent of this method in this forum admitted that he never tried it in a dual boot environment as he does not use Windows.

My advice is just don't use it.

***Third***, exactly what permissions do you want for this partition?

Linux will mount an ntfs partition with a "view" that gives it the appearance of having linux permissions when in fact it does not. The price you pay for this is that all permissions on every file will be exactly like th other.

Do you want everyone to be able to access all folders and files? Then something like this will work:
```
UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```

---

### Post by Bucky Ball on 2015-01-06
Do you have ntfs-config installed also? If so, you will find that in your Applications (in xfce4 is in 'Settings' as 'NTFS Configuration Tool'. That will re-write the /fstab for you. ;)

---

### Post by Morbius1 on 2015-01-06
I would also not recommend ntfs-config because it "will rewrite the /fstab for you".

[COLOR=#0000cd]**EDIT**[/COLOR]:
You don't want to use ntfs-config, Disks, or any other poorly written  application to touch fstab. The only person who should be editing it is  you.

I suggest templates and for ntfs it would look like the one I posted above.

You  could of course use the template the Ubuntu installer uses when you  select "something Else " at install time. It would look like this:
> #UUID=40F76A4E40B0C5CB /DataN          ntfs    defaults,umask=007,gid=46 0       0
Once  upon a time this worked without issue but back then all users where  automatically a member of the plugdev group ( gid=46 ). Today they are  not so you have to add then to plugdev to make them work.

---

### Post by Bucky Ball on 2015-01-06
> **Morbius1 said:**
> I would also not recommend ntfs-config because it "will rewrite the /fstab for you".

[COLOR=#0000cd]**EDIT**[/COLOR]:
You don't want to use ntfs-config, Disks, or any other poorly written  application to touch fstab. The only person who should be editing it is  you.

Had no idea there were problems with it. Always works faultlessly for me. Oh, well. Live and learn. Thanks for the tip, but what's the issue with it?

---

### Post by wyliecoyoteuk on 2015-01-06
If you must do this, you will need a separate data partition in windows, you do not want linux writing to your Windows system partition, or vice versa. 
This might help.
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by Vesnog on 2015-01-06
> **Bucky Ball said:**
> Do you have ntfs-config installed also? If so, you will find that in your Applications (in xfce4 is in 'Settings' as 'NTFS Configuration Tool'. That will re-write the /fstab for you. ;)

I do not have that tool installed and I prefer writing it manually :)

---

### Post by Vesnog on 2015-01-06
> **wyliecoyoteuk said:**
> If you must do this, you will need a separate data partition in windows, you do not want linux writing to your Windows system partition, or vice versa. 
This might help.
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Actually this is a separate DATA partition it is not the partition where the OS or the Bootloader reside.

---

### Post by Vesnog on 2015-01-06
> **Morbius1 said:**
> There are a number of issues with the path that you have selected.

***First***, mounting the Windows system partition from Linux as writable is always a dangerous thing to do. It would be better if you created a Windows data partition as ntfs and made that writable.

***Second***, the use of the "permissions" option is not as simple as just adding the option to the mount statement. You need to create what is essentially a conversion table on both Windows and Linux to convert user names from one system to the other. Without that you end up running the risk oh having this happen to you: 

My advice is just don't dot it. The original proponent of this method in this forum admitted that he never tried it in a dual boot environment as he does not use Windows.

My advice is just don't use it.

***Third***, exactly what permissions do you want for this partition?

Linux will mount an ntfs partition with a "view" that gives it the appearance of having linux permissions when in fact it does not. The price you pay for this is that all permissions on every file will be exactly like th other.

Do you want everyone to be able to access all folders and files? Then something like this will work:
```
UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```

I sometimes need to change the permission to run a script, execute or install a program for example without the permissions option, I cannot do that. I also do not want everything to have **chmod 777 **since when I use the file browser it just asks to execute every file which is a bit frustrating; therefore I used the options *fmask *and *dmask* for separate permissions on files and folders. What windows_names option does by the way? I am the only user on the Linux OS and Windows OS so I think this should not be that complicated.

---

### Post by Morbius1 on 2015-01-06
> I also do not want everything to have **chmod 777 **since when I use the file browser it just asks to execute every file which is a bit frustrating
Are you talking about something like this:
[ATTACH=CONFIG]259039[/ATTACH]
You can turn that off with this ( Edit > Preferences > Behavior ):
[ATTACH=CONFIG]259040[/ATTACH]
[COLOR=#0000cd]**Edit**[/COLOR]: "windows_names" prevents you in Linux from saving a file to the ntfs partition with a name that contains characters Windows does not recognize. Not a problem in Linux with these characters but Windows will ignore the file.

---

### Post by Vesnog on 2015-01-06
> **Morbius1 said:**
> Are you talking about something like this:
[ATTACH=CONFIG]259039[/ATTACH]
You can turn that off with this ( Edit > Preferences > Behavior ):
[ATTACH=CONFIG]259040[/ATTACH]
[COLOR=#0000cd]**Edit**[/COLOR]: "windows_names" prevents you in Linux from saving a file to the ntfs partition with a name that contains characters Windows does not recognize. Not a problem in Linux with these characters but Windows will ignore the file.
That is exactly what I was talking about apart from regular text files, photos and videos I have some source codes for interpreted languages so I need the executable bit set at least for me. However, I think files being readable, writable, executable by everyone to be a safety risk. Even for myself since I might execute something by accident, which is not likely to happen in Linux partitions. I also set the umask, dmask,uid and gid for these particular purposes.

---

### Post by Morbius1 on 2015-01-06
You have control over who has rwx by adjusting umask. So if you only want you to have it then change the line to this:
```
UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  defaults,nls=utf8,umask=077,uid=1000,windows_names 0 0
```
But if you ultimately want the ability to have one specific file marked executable and another not on an ntfs partition you have a complication because the standard way of mounting the partition does not allow that.

If you insist on pursuing the "permissions" option to accomplish this it's not as simple as adding the permissions option in fstab. Morbius in linux is different from Morbius in Windows. A "mapper" has to be created in both OS's that converts the morbius user in Linux with it's uid to a morbius user in Windows with it's sid.

You are making fundamental changes to the file and permissions structure of your Windows install to make it happen. I don't think that we ( and this is clearly my own opinion ) in the Ubuntu forum should be placed in the position to diagnose and remedy any filesystem problems you may experience in Windows by doing this. 

Your best bet is to seek guidance in the tuxera ( they created ntfs-3g ) forums if you want to pursue this option: [URL="http://tuxera.com/forum/"]http://tuxera.com/forum/



[/URL]

---

### Post by Vesnog on 2015-01-07
> **Morbius1 said:**
> You have control over who has rwx by adjusting umask. So if you only want you to have it then change the line to this:
```
UUID=01CCA0086DD8A980   /mnt/DATA                 ntfs  defaults,nls=utf8,umask=077,uid=1000,windows_names 0 0
```
But if you ultimately want the ability to have one specific file marked executable and another not on an ntfs partition you have a complication because the standard way of mounting the partition does not allow that.

If you insist on pursuing the "permissions" option to accomplish this it's not as simple as adding the permissions option in fstab. Morbius in linux is different from Morbius in Windows. A "mapper" has to be created in both OS's that converts the morbius user in Linux with it's uid to a morbius user in Windows with it's sid.

You are making fundamental changes to the file and permissions structure of your Windows install to make it happen. I don't think that we ( and this is clearly my own opinion ) in the Ubuntu forum should be placed in the position to diagnose and remedy any filesystem problems you may experience in Windows by doing this. 

Your best bet is to seek guidance in the tuxera ( they created ntfs-3g ) forums if you want to pursue this option: [URL="http://tuxera.com/forum/"]http://tuxera.com/forum/



[/URL]

I appreciate your effort, thanks for the help and the guidance I will also ask a similar question on that forum.

---

