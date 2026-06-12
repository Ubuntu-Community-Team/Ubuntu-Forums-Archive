---
title: "How to change the download folder location?"
date: 2017-03-01
forum: General Help
---

### Post by juntjoo2 on 2017-03-01
I manually moved it to another partition but when I click on it in a folder it's missing, well it's there but the system doesn't know that I moved it.

---

### Post by speartip on 2017-03-02
The locations of your home folders are controlled by Home/.config/user-dirs.dirs
You need to change the line that starts XDG_DOWNLOAD_DIR="/  to your new location.
Also make sure the partition you moved it to is mounted in the fstab file, otherwise your files wont show up until you manually mount the partition.

---

### Post by juntjoo2 on 2017-03-02
Thanks. I know I'm going to have trouble opening that so I'll need to go through the terminal. What's the command to open it? Thanks

---

### Post by speartip on 2017-03-02
No. No terminal required. Just go into your Home folder, view hidden files. then navigate to the file & edit it.

---

### Post by juntjoo2 on 2017-03-02
Thanks, but I don't see any .config files in there(??)

edit: okay, I found out how to see hidden files/folders, and found the config folder and the user-dirs.dirs file and changed the downloads path to "/media/ben/23F694AF726D13C3" which i got directly from the folder properties, but the system still thinks the folder is in the default location. hmm...

edit: the file says "# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported."

which might have something to do with it(?) IDK. that looks like gibberish to me.

---

### Post by speartip on 2017-03-02
I think you're mistakenly using the uuid, not the folder name.
eg. I have a separate partition that I have called storage, & I have my Downloads folder on that partition, so in my user-dirs.dirs file the path is:
XDG_DOWNLOAD_DIR="/storage/Downloads"
Does that help?

---

### Post by Impavidus on 2017-03-02
> **juntjoo2 said:**
>  and changed the downloads path to "/media/ben/23F694AF726D13C3" which i got directly from the folder properties, but the system still thinks the folder is in the default location. hmm...

That sounds like an automatically created mountpoint of an NTFS partition, created when you used the GUI to mount that partition. That may be a problem if you want to use the downloads directory but forget to mount the partition first. It may be better to use fstab to automatically mount the partition during boot.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You may have to logout and login before the changes work.

---

### Post by juntjoo2 on 2017-03-22
thanks.  correct me if i'm wrong but it looks like the system thinks the folder is in the default locations 'home/ben/downloads/' then gives me the error.  so I'm thinking if I could just change where it's looking for the folder, which I can manually navigate to, presumably then it should be able to do from the right command from the right file no?  maybe I have the wrong file?

```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/media/ben/23F694AF726D13C3"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

maybe i got the syntax wrong?

---

### Post by yancek on 2017-03-22
I've never done this myself but, if you look at the example 'Speartip' posted from his config file and compare it to yours, you see 'Downloads' is missing from the end of your entry.  

> changed the downloads path to "/media/ben/23F694AF726D13C3" 

The above is pointing not to your Downloads directory but to the root of the windows partition.  Not sure why you would put your Ubuntu Downloads folder on a windows partition?

---

### Post by Dennis N on 2017-03-22
Most downloads of files are instigated from within a browser. If you want to change the Firefox download directory, that can be set to override the system setting in Preferences > General > Downloads. In Chromium, it can be set in Settings > Advanced > Downloads.

That may be all you need?

---

### Post by juntjoo2 on 2017-03-23
thanks, but actually now I want to move the Home folder or just some folders inside it to a separate partition that these folders with my Windows installation so I don't have to have two copies for each file that I want to access from both systems

it's starting to look like the solution "impavidus" from above suggested is what I may need to do...

it's not a windows one, just a separate one.  Trying to have a separate set of folders that both Linux and Windows will share, downloads, pics, videos, etc

---

### Post by speartip on 2017-03-23
If you want to share it between windows/ubuntu it will have to be an NTFS partition as windows cannot read ext4.
Then you need to have that partition mounted in fstab. This tutorial may help:
[https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions](https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions)
The bit under FSTAB is what you need.

---

### Post by juntjoo2 on 2017-03-23
> **yancek said:**
> I've never done this myself but, if you look at the example 'Speartip' posted from his config file and compare it to yours, you see 'Downloads' is missing from the end of your entry.  



The above is pointing not to your Downloads directory but to the root of the windows partition.  Not sure why you would put your Ubuntu Downloads folder on a windows partition?


check
this out: 

[IMG]http://i.imgur.com/pu7NqdS.png[/IMG]

it shows that default location even though in the directory file I edited shows different.  So I'm wondering if I've got the right file. I'm thinking I need to get at that file that is responsible for that pop up message there, then of course get the address correct as you pointed out.

> **speartip said:**
> If you want to share it between windows/ubuntu it will have to be an NTFS partition as windows cannot read ext4.
Then you need to have that partition mounted in fstab. This tutorial may help:
[https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions](https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions)
The bit under FSTAB is what you need.


I
don't think it's ext4 as I can access it from windows.  do you think it is for some reason?

---

### Post by vasa1 on 2017-03-23
Please post the output of```
sudo fdisk -l
```

---

### Post by juntjoo2 on 2017-03-23
> **speartip said:**
> If you want to share it between windows/ubuntu it will have to be an NTFS partition as windows cannot read ext4.
Then you need to have that partition mounted in fstab. This tutorial may help:
[https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions](https://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions)
The bit under FSTAB is what you need.


Thanks.

I'm working on this now but on another page it says: 

The following commands will duplicate your current fstab, append the year-month-day to the end of the file name, compare the two files and open the original for editing.
1. Duplicate your fstab file:
sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)2. Compare the two files to confirm the backup matches the original:
cmp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)3. Open the original fstab in a text editor:
sudo gedit /etc/fstab and add these lines into it
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=????????   /media/home    ext3          defaults       0       2 and replace the "????????" with the UUID number of the intended /home partition.


What's this all about and is it necessary? I think I will just try the link you suggested as it looks simpler but I just wanted to mention this in case it might be important.

> **vasa1 said:**
> Please post the output of```
sudo fdisk -l
```

```
Device     Boot     Start       End   Sectors   Size Id Type/dev/sdb1            2048  26626047  26624000  12.7G 27 Hidden NTFS WinRE
/dev/sdb2  *     26626048  26830847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdb3        26830848 149709734 122878887  58.6G  7 HPFS/NTFS/exFAT
/dev/sdb4       149710848 976773119 827062272 394.4G  f W95 Ext'd (LBA)
/dev/sdb5       866660352 969060351 102400000  48.8G 83 Linux
/dev/sdb6       969062400 976771071   7708672   3.7G 82 Linux swap / Solaris
/dev/sdb7       149712896 866658303 716945408 341.9G  7 HPFS/NTFS/exFAT
```

hmm.. how come it is represented twice.  I know I don't have enough space to have both those large partitions.  and for the uuid which would I use?

actually, doesn't look like sbd4 is shown under

```
ben@Hal:~$ sudo blkid/dev/sdb1: LABEL="PQSERVICE" UUID="DAA41C49A41C2B11" TYPE="ntfs" PARTUUID="0baf0baf-01"
/dev/sdb2: LABEL="SYSTEM RESERVED" UUID="2878747C78744B18" TYPE="ntfs" PARTUUID="0baf0baf-02"
/dev/sdb3: UUID="A85C91B55C917F2E" TYPE="ntfs" PARTUUID="0baf0baf-03"
/dev/sdb5: UUID="4c8a3d4c-9494-419d-8845-b91fa0b22ee9" TYPE="ext4" PTTYPE="dos" PARTUUID="0baf0baf-05"
/dev/sdb6: UUID="6787177f-c844-4144-8f74-af4118ea719e" TYPE="swap" PARTUUID="0baf0baf-06"
/dev/sdb7: UUID="23F694AF726D13C3" TYPE="ntfs" PARTUUID="0baf0baf-07"
```

I'm confused about this step here from the fstab page:

```
For example : /media/windows

sudo mkdir /media/windows
```

to make the mount point. In that code how does it tell the computer to make the mount point/folder in the proper partition?

oh I think I get it.  It's like, 'virtual'.

having trouble adding this "mount point".  I'm trying to add it calling it "shared files" so I tried without quotes at first and it only saw "shared" and thought "files" was the file system, understandably, so  I put it in quotes next time in fstab but that didn't work either.  How do you get around this?


well, whatever, I just named it "sharedFiles" which seemed to work.  what about this though?

[IMG]http://i.imgur.com/NQUYkBO.png[/IMG]

that was an old reference to that partition which I've now connected to my "shareFiles" mount point so when I click it an error comes up.  I don't even know how it got in that side bar there.  I wasn't there before today and I did a lot of things today so far I didn't know what I was doing. But anyway, "remove" is greyed out.  Anyone know how to remove it?


And then moving along, I want these side bar links to "home" "pictures" and what not to lead to my new separate partition.  And on the page that explains how to do this it says:

Copy /home to the New Partition

Next we will copy all files, directories and sub-directories from your current /home directory into the new partition. If you do not have an encrypted home file system, just do the following:

sudo rsync -aXS --exclude='/*/.gvfs' /home/. /media/home/. I prefer adding the "--progress" tag just before the "--excludes" one - otherwise there is no indication of anything happening. The "--progress" tag reports on each file individually so you see tons of unfamiliar stuff scrolling by very fast. Rsync can be interrupted as many times as you like and it checks to see how much has already been done when you start it up again. So, this copying stage can be broken down into many sessions. After it has completed once it's wise to run it a couple more....

And this is where my brain short circuited.  And unfortunately there are a lot more steps beyond this point.  It's this page: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Can't I just drag over my files, cut them then paste them into my new folder once I create my new folders in my new partition?

Maybe someone can explain simply what I should do next? For all I know I could be on the wrong page.  I want as I mentioned earlier for these side bar buttons, for these folders to be relocated in my "sharedFiles" partition.  Am I on the right page?  I can do what I normally do when stuck and short on time and just follow the instructions to a T with my fingers crossed that I'm doing the right thing but I prefer to understand what I'm doing if possible before I do it. So just tell me if I should just follow these instructions  I guess. I just never know if I'm wasting my time and that there is a simpler method like finding some file and replacing the directory for a folder and editing it to the new directory.  often solutions for ubuntu are long pages of stuff I can barely read.

---

### Post by vasa1 on 2017-03-23
You can upload images directly by clicking on the paper clip icon above the posting area. No need for linking to third-party image-hosting sites :)

See point #4 in the Forum's [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945").

Also, please use "Quote" tags when including material copied from elsewhere and give proper credit to the source in the form of a link to the source.

---

### Post by speartip on 2017-03-23
[SIZE=2]I don't think you can use 2 words like that. Try:
```
sudo mkdir /shared_files
```
That creates the directory in your root folder. To take ownership of that folder you will need to do:
```
[COLOR=#00000a][FONT=Noto Sans]sudo chown -R username:username /shared_files[/FONT][/COLOR]
```
Changing "username" for your own username of course.
Then something like:
```
[COLOR=#00000a][FONT=Noto Sans]sudo chmod -R 755 /shared_files[/FONT][/COLOR]
```
Then reboot to take effect.[/SIZE]

---

### Post by juntjoo2 on 2017-03-23
actually, I found that under the "bookmarks" tab in the file explorer you can easily change the directory for your downloads folder and other bookmarks already there or that you add to the list.

actually that didn't do it either.  

this is what I did to my directories file:

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/sharedFiles/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="/sharedFiles/Documents"
XDG_MUSIC_DIR="**/sharedFiles/Documents/Music**"
XDG_PICTURES_DIR="/sharedFiles/Documents/Pictures"
XDG_VIDEOS_DIR="/sharedFiles/Documents/Videos"

yet...

[ATTACH=CONFIG]274276[/ATTACH]

I've seen this solution elsewhere so it looks like it is the correct one but for some reason this directory file doesn't seem to be affecting these "places" in my sidebar as you can see in the pic.  They still are looking for the default location, which according to my edits I've changed so that leads me to wonder what file they are looking to(??)


oh no! never mind.  a restart solved the problem. silly me. Thank you guys for helping me though out all of this.

apparently moving your desktop isn't as easy.  Anyone know about this or is it just me? It's in the user directory list and I edited it just like the others but I ran into problems.

---

### Post by speartip on 2017-03-24
I never move the Desktop Folder. It's nearly pointless, unless for some reason you store files & folders there.
Just a thing. Why are you moving,  everything into your Documents folder?

---

### Post by speartip on 2017-03-24
Entirely your choice, but I would have it like this:

  	 	 	 	   XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/sharedFiles/Downloads"
XDG_TEMPLATES_DIR="/sharedFiles/Templates"
XDG_PUBLICSHARE_DIR="/sharedFiles/Public"
XDG_DOCUMENTS_DIR="/sharedFiles/Documents"
XDG_MUSIC_DIR="/sharedFiles/Music"
XDG_PICTURES_DIR="/sharedFiles/Pictures"
XDG_VIDEOS_DIR="/sharedFiles/Videos"

---

### Post by juntjoo2 on 2017-03-24
I don't have a lot of just "documents" so I just use that as a general category for all my stuff. I don't really have an effect plan on how I want to organise everything and I don't even keep much but I just want it all separate from one system and actually downloads and my desktop are my most used folders as I download a lot then delete and create and toss a lot of other stuff on my desktop first before sending them to their proper final homes and to have a universal desktop would be a bit more efficient

> **speartip said:**
> Entirely your choice, but I would have it like this:

  	 	 	 	   XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/sharedFiles/Downloads"
XDG_TEMPLATES_DIR="/sharedFiles/Templates"
XDG_PUBLICSHARE_DIR="/sharedFiles/Public"
XDG_DOCUMENTS_DIR="/sharedFiles/Documents"
XDG_MUSIC_DIR="/sharedFiles/Music"
XDG_PICTURES_DIR="/sharedFiles/Pictures"
XDG_VIDEOS_DIR="/sharedFiles/Videos"

So far that's the only place that seems to work for desktop. Try putting it somewhere else your actual desktop will open up to the folder above which is home I think. As if another script/file looks for desktop inside home and overrides the user directory file, doesn't find it then just settles for the next folder up to display being home. So maybe someone will know how to edit that. I'll do a search...

no luck and now for some reason, although my downloads folder works in it's new spot every time I log into ubuntu I get this:

[ATTACH=CONFIG]274286[/ATTACH]

What's blueman services?  And why is it having issues?

---

### Post by vasa1 on 2017-03-24
> **juntjoo2 said:**
> no luck and now for some reason, although my downloads folder works in it's new spot every time I log into ubuntu I get this:

[ATTACH=CONFIG]274286[/ATTACH]

What's blueman services?  And why is it having issues?
It has to do with Bluetooth.

See what choices you get when you run```
blueman-services
```

This is what I see first (bt1) and then what I see when I click on "Downloads" (bt2).

---

### Post by jeremy31 on 2017-03-24
You need to change the default folder for files received using bluetooth, blueman-services should bring up this screen

---

### Post by juntjoo2 on 2017-03-24
I'm getting 
[ATTACH=CONFIG]274290[/ATTACH]
neither folder produce anything on the right side.

and here's some possibly helpful info:

```
ben@Hal:~$ blueman-servicesblueman-services version 2.0.4 starting
_________
load_plugins (/usr/bin/blueman-services:91)
['Network', 'Transfer'] 
_________
set_page (/usr/bin/blueman-services:138)
Set page Network 
wlp2s0
Traceback (most recent call last):
  File "/usr/bin/blueman-services", line 165, in on_selection_changed
    self.set_page(id)
  File "/usr/bin/blueman-services", line 149, in set_page
    inst.on_load(self.container)
  File "/usr/lib/python3/dist-packages/blueman/plugins/services/Network.py", line 43, in on_load
    self.setup_network()
  File "/usr/lib/python3/dist-packages/blueman/plugins/services/Network.py", line 206, in setup_network
    avail_plugins = applet.QueryAvailablePlugins()
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 654, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 246, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
dbus.exceptions.UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: QueryAvailablePlugins is not a valid method of interface org.blueman.Applet


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.



```

---

### Post by vasa1 on 2017-03-24
> **juntjoo2 said:**
> I'm getting 
[ATTACH=CONFIG]274290[/ATTACH]
neither folder produce anything on the right side.

...
Yikes!

I'm no good at Bluetooth issues. I hope someone can figure out why you aren't seeing anything.

---

### Post by jeremy31 on 2017-03-24
Post results for ```
hciconfig -a; rfkill list
```

---

### Post by juntjoo2 on 2017-03-24
> **jeremy31 said:**
> Post results for ```
hciconfig -a; rfkill list
```

```
ben@Hal:~$ hciconfig -a; rfkill listhci0:	Type: BR/EDR  Bus: USB
	BD Address: 18:F4:6A:D8:62:95  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:715 acl:0 sco:0 events:57 errors:0
	TX bytes:5788 acl:0 sco:0 commands:57 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'Hal'
	Class: 0x3c0000
	Service Classes: Rendering, Capturing, Object Transfer, Audio
	Device Class: Miscellaneous, 
	HCI Version: 3.0 (0x5)  Revision: 0x25b
	LMP Version: 3.0 (0x5)  Subversion: 0x4203
	Manufacturer: Broadcom Corporation (15)


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

thanks

---

### Post by jeremy31 on 2017-03-24
Search Dash for personal file sharing, disable receive files over bluetooth.  Reboot, then see if it can be reenabled through Personal File Sharing

---

### Post by juntjoo2 on 2017-03-24
> **jeremy31 said:**
> Search Dash for personal file sharing, disable receive files over bluetooth.  Reboot, then see if it can be reenabled through Personal File Sharing

[ATTACH=CONFIG]274294[/ATTACH]

what do you think?

---

### Post by jeremy31 on 2017-03-24
Do you see anything different if you right click on the Blueman icon and select Local Services?

---

### Post by juntjoo2 on 2017-03-24
> **jeremy31 said:**
> Do you see anything different if you right click on the Blueman icon and select Local Services?

which
icon?  I've never seen it anywhere else.  btw I looking through my apps and found a startup manager and in there turned it off.  By this time I forgot how I even got here.  it doesn't look like it will bother me again unless something else happens but do I need it for anything?  Is it necessary for general bluetooth connections?  if so maybe I should start another thread?  If not, can I delete it entirely?

---

