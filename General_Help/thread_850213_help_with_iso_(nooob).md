---
title: "help with iso (nooob)"
date: 2008-07-05
forum: General Help
---

### Post by lilgoo19 on 2008-07-05
is there any way to mount an iso to an internal hard drive, then run that iso from that hard drive? if you can help, please simplify it, im new to this

---

### Post by scragar on 2008-07-05
try installing gmountiso, it's a very simple tool that automates the entire procedure.


for best results the mount point should be an empty folder, normally this would be /media/cdrom0 for most CDs/DVDs

---

### Post by lilgoo19 on 2008-07-05
will that mount the iso directly to the hard drive?
what i need to do is take an operating system iso, and install that OS from the iso, because my dvd drive is broken

---

### Post by scragar on 2008-07-05
oh, it won't do that, but you can extract the contents of the .iso to the hard drive, and that should let you boot from it, although you will need to add the boot flag and such to the hard drive before that will work.

---

### Post by lilgoo19 on 2008-07-05
ok, how would i do that? im pretty new to linux

---

### Post by scragar on 2008-07-05
ubuntu offers the extract here option on the context menu, alternativly you could open it using the archive manager, I would recomend moving the iso to the HD before using the extract here option though, just to make things easier.

---

### Post by lilgoo19 on 2008-07-05
ok, i have no clue what 90% of the stuff you just said was.
i have the iso on my desktop, now where would i go from there to get it to be able to boot the installation from my hard drive

---

### Post by lswb on 2008-07-05
Check out the man page for the mount command, with the loop option, you can google for more details, basically it' something like:


mount -t iso9660 iso.image /mountpoint -o loop;

Also, going from memory here, but I believe just right-clicking on the image from gnome desktop (probably kde also), you can select the option to open it with archive manager, and from there you can view or copy individual files.

As far as using the image to install an OS, I'm not certain if that is possible, but it certainly is NOT possible to install the OS to the partition where the image is mounted. It MAY be possible to copy the iso image to a separate partition and somehow get that partition to boot, then install the OS to a different partition, but I wouldn't be too hopeful. Can you put the image on an thumbdrive and burn a CD on another computer? Maybe a local library will allow you to do this.

---

### Post by lilgoo19 on 2008-07-05
crap, any other ways? i really need help, and im a complete noob with linux.  i really have to have this done asap.

---

### Post by avtolle on 2008-07-05
Take a look at [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) assuming you have a version of Windows running.

---

### Post by lilgoo19 on 2008-07-05
i have ubuntu, and i backed up my windows xp just in case, and the disk broke for xp, along with my dvd drive

---

### Post by sande87 on 2008-07-06
im doing much the same thing. im currently working on a script that will do iso mounts for me. Im fairly new to linux too, so I know how you feel.

if you need to copy the contents of you iso onto you harddrive you can to the following. PS! you need to have superuser privileges is some form, su or sudo will both do.

sudo mkdir /media/my_iso
sudo chmod 555 /media/my_iso 
sudo mount -o loop $ISO_PATH /media/my_iso -t iso9660

$ISO_PATH stands for where your iso image is on your dirve. for example /home/sandman/ubuntu.iso, is one of the iso's on my drive. so if I wanted to mout that iso, Id to this in console.

sudo mkdir /media/ubuntu
sudo chmod 555 /media/ubuntu
sudo mount -o loop /home/sandman/ubuntu.iso /media/ubuntu -t iso9660

after that there should be a CD icon on you desktop with the contents of you iso. then all you need to do is copy the contents onto an empty USB device.

feel free to mail me at [email]mikal.sande@gmail.com[/email] if you need more help :)

---

### Post by VMC on 2008-07-06
> **lilgoo19 said:**
> will that mount the iso directly to the hard drive?
what i need to do is take an operating system iso, and install that OS from the iso, because my dvd drive is broken

That's often referred to as a "[Poor Man's Install]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=99q&q=Poor+Man%27s+Install&btnG=Search")". Here's a googled link with lots of options.

Here's another using ubuntu. It's older info but still applies:
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

