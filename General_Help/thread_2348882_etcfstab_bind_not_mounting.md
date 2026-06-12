---
title: "/etc/fstab bind not mounting"
date: 2017-01-08
forum: General Help
---

### Post by jbb1996 on 2017-01-08
I am trying to mount a folder on startup with /etc/fstab but i keep getting this error 

mount: /etc/fstab: parse error at line 14 -- ignored
this is my /etc/fsta file
```

# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md2p1 during installation
UUID=ad1778e8-e9b7-45ae-8f81-fbf8a3706aba /               ext4    errors=$
# /boot was on /dev/sda3 during installation
UUID=9afb8b41-2060-4d62-96cb-550d89bc8c6f /boot           ext4    default$
# /home was on /dev/sda2 during installation
UUID=a26553c2-6982-43fc-a821-4571d0605295 /home           ext4    default$
/steam  /home/johnny/.steam/    none defaults,  bind 0 0



```

---

### Post by efflandt on 2017-01-08
Is it my imagination (or font) or is there a space between "defaults," and "bind"? There should be no spaces in the list of options.

johnny would also need read-write permission for /steam.

---

### Post by jbb1996 on 2017-01-09
thanks for the reply 


I do have read and right permission for /steam.
there was a space so I removed it and no longer get the error but it still doesn't mount the folder.

if i run mount manual
 ```
sudo mount --bind /steam /home/johnny/.steam/
```
it works with no errors.

the line in /etc/fstab now looks like
```
/steam /home/johnny/.steam/ none defaults, bind 0 0
```

---

### Post by chris354 on 2017-01-09
I think your issue may be the trailing slash.

Try this
```
/steam /home/johnny/.steam none defaults,bind 0 0
```

---

### Post by jerome1232 on 2017-01-09
You still have a space between defaults, and bind.

There should be no space after the comma. The defaults option is redundant anyways.

This is functionally equivalent to doing it with the defaults option specified.
```
/steam /home/johnny/.steam none bind 0 0
```

---

### Post by jbb1996 on 2017-01-11
Thanks for the replays.

I tried 
```
/steam /home/johnny/.steam none bind 0 0
```

but it still will not mount on boot

---

### Post by jerome1232 on 2017-01-11
What about if you run (after having boot up etc)
```
sudo mount -a
```

Are there any errors? Is it mounted after running that?

---

### Post by jbb1996 on 2017-01-11
OK so I have been trying to get it to work for 3 hours now :( still no luck.

if I delete ~/.steam reboot and then make a new ~/.steam folder and then run
```
sudo mount -a
```
it works with no errors but when I reboot it is not mounted and when I run
```
sudo mount -a
```
it does nothing

---

### Post by geeksmith on 2017-01-11
Could it be that /home isn't yet mounted when it tries to bind mount /steam? I see that home is on a separate filesystem in your fstab.

You could try putting the bind mount command in /etc/rc.local, perhaps after sleeping for a couple seconds.

---

### Post by jbb1996 on 2017-01-11
that should not be the problem because the /home is mounted on the line before.    

there is no /etc/rc.local file on my system should I make one?

---

### Post by yetimon_64 on 2017-01-11
> **jbb1996 said:**
> ...there is no /etc/rc.local file on my system should I make one?

If you used the file manager to look for that file it can be difficult to find. It is not necessarily listed purely alphabetically, but can be sorted by file type and can be tucked away in the first couple of lines of file icons when you would usually look further down the folder for an alphabetical listing for it making it hard to spot at times.

Double check with the terminal...
```
ls -l /etc/rc.local
```
If you get a response like ...
> ```
$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 306 Dec  6 05:07 /etc/rc.local
```... then the file exists, but is just hard to spot in the file manager. 


Or, if you want to edit it, you can use the terminal to launch an editor with the file itself as root ...
```
sudo -H gedit /etc/rc.local
```
Note the "-H" switch with sudo is for launching gedit, a graphical application, as root correctly.

As /etc/rc.local is a standard OS file I fully suspect it is there but being a bit hard to find as a result of file manager file sorting etc. Cheers, yeti

---

### Post by geeksmith on 2017-01-11
Sure, doesn't hurt to create the file and try it. Just make sure you set the execute bits.

If "mount -a" works after the system has started but doesn't work during boot, then I still suspect some timing problem. Can't think of another reason it would fail to mount.

Do you see any errors while booting? Does "sudo journalctl -xe" give any clues?

---

### Post by DuckHook on 2017-01-11
@OP

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

You have been using [noparse]>  and [/noparse] tags which are not the same.

---

### Post by jbb1996 on 2017-01-13
sorry about the code tags I am new to the forum 

I did check for /etc/rc.local with
```
[COLOR=#000000][FONT=&quot]ls -l /etc/rc.local[/FONT][/COLOR]
```
and it is not there.

there is no error on boot and there is nothing in [COLOR=#000000]
[/COLOR][COLOR=#000000]sudo journalctl -xe

[/COLOR]but I think I have figured out what the problem is when I reinstalled my OS I encrypted my home folder so it will not find ~/home/ intel I login in to my user account

---

### Post by DuckHook on 2017-01-14
So far, you have been wrestling with one strategy trying to bind mount to an encrypted directory. Two items of note:

[LIST=1]
[*]Yours is a good example of why it is important to disclose as much information as possible when asking for help. The encrypted /home is very important info.
[*]Your approach may be unnecessarily complex. I take it that your steam data is on a separate partition/directory and you want ~/.steam to point to it. Instead of trying to bind-mount this directory in your fstab, just symlink to it and avoid fooling around in fstab altogether:```
cd ~
``````
ln -s /steam .steam
```You will now have a softlink to the directory you want in your home directory called *.steam*.  Before creating the symlink, you must delete the bind-mount in fstab and reboot. The symlink will not be created if ~/.steam already exists.
[/LIST]
As has already been noted, spaces (or lack of) are very important in Linux, so make sure you type in my code without error. Copy and paste if necessary.

The advantage of a symlink is obvious: its existence is not dependent on your /home directory being decrypted. After all, you will never need access to this directory until after you log in anyway.

---

### Post by igdfpm on 2017-01-14
Where exactly is the "/steam" folder you are trying to mount located? According to your current fstab it is a folder on your root partition - is that actually correct? If it is elsewhere you will need to do a "2 stage" **mount** then **bind** ... I keep all my media folders on separate partitions - makes it easy to share amongst distros so have lines similar to the example below in my fstab ;)

```

# /dev/sdb8 LABEL=LOCAL-VIDEOS
# mount LOCAL-VIDEOS in /mnt then bind folder to $HOME/Videos

# Stage 1
UUID=b5702ffd-fff4-4bb5-ad36-95a42ac59b2f	/mnt/VIDEOS     	ext4	rw,relatime,data=ordered	0 0

# Stage 2
/mnt/VIDEOS/Videos 							/home/taz/Videos none 	defaults,bind 0 0

```

---

### Post by jbb1996 on 2017-01-15
I will try the [COLOR=#000000]symlink the [/COLOR]reason I was using bind mounting is I have read that some steam games do not work with it but I will give it a try

---

### Post by DuckHook on 2017-01-15
> **jbb1996 said:**
> I will try the [COLOR=#000000]symlink the [/COLOR]reason I was using bind mounting is I have read that some steam games do not work with it but I will give it a try
Yes, I would suggest giving the symlinking solution a try first. If indeed this breaks some steam games, then you can still bind-mount, but I would recommend not doing so in fstab. It is easy enough to write a simple script that you can leave on your desktop. Once logged in, you can mount by activating the script.

Good luck and Happy Ubuntu-ing!

---

