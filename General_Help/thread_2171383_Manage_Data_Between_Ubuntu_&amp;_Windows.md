---
title: "Manage Data Between Ubuntu &amp; Windows"
date: 2013-08-30
forum: General Help
---

### Post by ktz84 on 2013-08-30
**Updated Question in Post 6**

I have nearly 3TB of data which will be split over 3 physical disks and numerous partitions. All Video will consume 1 2TB hard disk plus I'll make a bit of space available on this drive so I can move the swap off the SSD where my main Ubuntu install is.

In windows I know what I'm doing. I just move the location of any of profile folders and they still all show in my profile even though they are spread all over numerous disks. I'm sure I must be able to do something similar in Ubuntu.

At the min I'm in the process of moving all my data of ntfs to ext4 partitions which I have names like Movies, TV, Other Video, Music, VM, Pictures, Documents, EBooks, Ownlcoud, etc. How do I go about linking all those partitions to my home folder?

---

### Post by lukeiamyourfather on 2013-08-30
I would suggest not going overboard with the partitions. It's unnecessarily limiting yourself, because what happens if you run out of space on the "Video" partition and you still have hundreds of gigabytes free on other non-contiguous partitions? I'd use one large partition to store that kind of data and simply mount it as /home during the install.

---

### Post by vanadium on 2013-08-30
> **ktz84 said:**
> How do I go about linking all those partitions to my home folder?

Just by ... linking. You can graphically create links by holding Alt+Shift pressed and then dragging the icon of the folder to where you want the link. With the command line, one uses the "ln" command. A link in linux for practical purposes behaves as if it were a real directory. Links allow you to conveniently arrange the data structure the way you want, without the need to move the data physically around.

---

### Post by oldfred on 2013-08-30
I mount partitions and link folders into my /home, so they look like the standard folders in Ubuntu. I use mount but first link also has Morbius1suggestion on using bind.
I have used links from both NTFS and Linux formatted partitions, but you have to set ownership & permissions with Linux and with NTFS have correct settings in fstab entry as default permissions.
   

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by btindie on 2013-08-30
Take a look at [LVM]("https://wiki.ubuntu.com/Lvm") as it allows you to have multiple partitions that can be resized on the fly.

You can either define each physical drive in it's own volume_group or you can put all drives in the same volume_group creating one large storage pool. From that you can then split it into logical_volumes which are the equivalent of partitions under LVM, so you'd then create a filesystem on it - e.g. ext4

Install *system-config-lvm* for a gui tool to configure it, though it's easy enough to do it from the command line.

Basic LVM [tutorial]("http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/")

---

### Post by ktz84 on 2013-08-30
Ok I think I need to think about this a bit more closely.

What I have at the minute is a dual boot system. Windows 7 and Ubuntu. Ubuntu 13.04 x64 is to be my primary OS. I have imaged my current Windows setup and converted it to a vmdk which I have setup and can run in VMWare Player in Ubuntu and VMWare Workstation 9 in Windows 7. I have only started using this setup so I am not confident enough to rely on Windows 7 on a VM to do everything that I might need Windows for so I will continue to dual boot for the time being. I have my data all separated from all OSes because I like that distinction and also because it is going to be necessary in order to try and get all this working together and maintain access to files from all OSes.

The bulk of my data is managed by several programs.

1) Plex Media Server for Movies, TV, Other Video & Music (currently on Windows 7)
2) Calibre for eBook Collection (currently on Windows 7)
3) Owncloud (currently on Xubutu VM which also manages multiple google drives syncs)
4) Apache2, PHP & MySQL for Wordpress, Owncloud Management & OpenCart) on same Xubuntu VM

I don't currently have anything specific to manage photos. I never really look at my photos much which is why I probably haven't looked at this yet.

I would be considerably better off with a NAS and I probably will get this a some stage but I haven't got one at present so I will have to work with what I do have.

I'm totally conflicted about what way I can manage all this and have all data available from all servers/programs. My initial plan was to move everything over to ext4 and mount drives in Ubuntu hence my initial question here however now I realise that this probably doesn't work with my Native Windows 7 install even if I maintain PMS and Calibre on both Windows 7 and Ubuntu as the Ubuntu ext4 will not be seen by native Windows 7 so there will be no data for PMS or Calibre to see. I'm right on that aren't I?

The next thing I'm now thinking is move PMS & Calibre to the Xubuntu VM and add split the data over several vmdk so that any data corruption will be confined to just that vmdk. I have a gigabit wired network and VMWare recognises that so transfers should be adequate.

The other option is to leave the data in ntfs as that can be seen by both Windows & Ubuntu and can be mounted in Xubuntu VM.

Anybody any advice on the best approach for all this?

---

