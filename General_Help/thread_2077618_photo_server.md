---
title: "photo server"
date: 2012-10-29
forum: General Help
---

### Post by LT72884 on 2012-10-29
Hello all. I just need some direction. I have about 5 or 6 hard drives floating around my house. SOme are ide others are sata. i would like to use them strictly for storage. the only items that will be stored on them, photos, music, documents and thats it. i have another drive strictly for movies. 

here are the drives as follows:

2 40GB sata drives
1 IDE 30gb
1 IDE 20gb

I do not want to waste them and need a way to save to them from my laptop or desktop. This is where i need help. I need an easy way to access them from windows machine. they need to stay active and not drop off the face of the earth. i need an easy config. i was thinking freenas but that is more of a business solution. Basically, what is the best,smallest,simpliest file server option for a old school pc that has an amd 2800 plus and 256 MB ram?

tahnks

Matt

---

### Post by shreepads on 2012-10-29
Why not just use Samba? Can be managed within Nautilus 'shared folders'...

---

### Post by 2F4U on 2012-10-29
Ubuntu Server plus Samba would a possible direction. Your PC would fit the minimum requirements for Ubuntu Server without GUI:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by loganfre on 2012-10-29
You might also want to check out [Greyhole]("http://www.greyhole.net/"). It adds drive pooling and redundancy to Samba shares.

---

### Post by LT72884 on 2012-10-30
hmm. all right guys. i may have to check it out. just got home from calc class and had forgotten bout this. haha. i was thinking of either adding them to my main pc and mapping the drives or a server

---

### Post by LT72884 on 2012-10-30
> **LT72884 said:**
> hmm. all right guys. i may have to check it out. just got home from calc class and had forgotten bout this. haha. i was thinking of either adding them to my main pc and mapping the drives or a server

thanks for all the help so far. im thinking either a file server or mapping the drives through windows. Just wish i could make it accessible from anywhere though with out to much hassle. I guess team viewer for windows would work if i installed the drives to the windows box. Or use putty, but then i have to download a client and all that stuff. arg. haha

---

### Post by LT72884 on 2012-10-31
Ok an update. I found some ram. i have 1gb of ram now and i found 4 other drives. so now i have 3 sata drives and 4 ide drives. i have close to a TB of space between those drives BUT i do have a 500gb sata drive that is in an external enclosure and one in a sliding docking station sort of thing. I was thinking of either making a file server for storage that is remotly accessable somehow from windows machines or buying a docking station such as this one

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5352947&CatId=2785](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5352947&CatId=2785)

except the one in the link is the wrong one. i found one tht is sata and ide

basically, i dont want to waste these drives and i do need storage space. 
just trying to figure this out the best possible way. if i go server way, i need it to stay reliable, accessable from anywheres in world, easy config and easy for wife to navigate to from windows vista laptop

thanks guys

Im just confused and exhausted. haha

---

### Post by loganfre on 2012-11-01
> **LT72884 said:**
> basically, i dont want to waste these drives and i do need storage space. 
just trying to figure this out the best possible way. if i go server way, i need it to stay reliable, accessable from anywheres in world, easy config and easy for wife to navigate to from windows vista laptop

If you want to access your files over the web you either need to use ftp/sftp or a VPN. Both are described in the [Server Guide]("https://help.ubuntu.com/12.10/serverguide/index.html").

Logan

---

### Post by LT72884 on 2012-11-01
> **loganfre said:**
> If you want to access your files over the web you either need to use ftp/sftp or a VPN. Both are described in the [Server Guide]("https://help.ubuntu.com/12.10/serverguide/index.html").

Logan

ok cool. i will read up on that. im still trying to decide what is best. external drives mapped over network cuz i can turn them off and they are portable, or a file server. i will need to turn the server off at night when it is not in use cuz i dont want the drives to go out. haha. 

thanks guys

---

### Post by LT72884 on 2012-11-02
Ok, i found a case and some ram. i am going to make a file server. Couple of questions though. Here is what i would like to do. I will install ubuntu server, get samba set up, create a folder named netdrive, and setup ssh. Then on my winxp home and pro machines, ill map a network drive to //192.168.x.x/netdrive
ill make sure the netdrive directory has full permissions for my wife and i. 

a couple of questions:

My wife wants to if you can password protect the netdrive folder so that everytime she double clicks the mapped drive, it asks for a password. she doesnt want others to see her stuff?

She wants to be able to access it from others houses. so i was thinking ssh but she doesnt know how to use command line at all and is used to sites like photobucket. you can see the image before you download it. does ssh have a GUI that can display thumbnails of the contents?

Last question, Since i will have 4 IDE drives in the server, and 2 usb drives, does ubuntu read those as seperate drives like windows does? or when ubuntu monts them, they become one giant drive sorta speak? The reason i ask, if i have folders on each drive that need to be accessed, IE, music 1 one ide 1, music 2 on ide 2 etc etc. How do i map those in winxp? same way? //192.168.x.x/music 2 and ubuntu server will know which drive to map it to?
If i remember how FSH works, i can mount the drive anywhere i want to. so for example, everything thing in linux goes under "/" so i can mount all my drives to the same mount point such as /home/matt/netdrive. Will that work or will i have to mount each drive(partition) to its own folder? IE /home/matt/netdrive1,
/home/matt/netdrive2 etc etc? I would like only one folder to show up on the winxp machine. kind of good house keeping. DOnt want to do raid but maybe links or something. symlinks could work i guess.

EDIT. Since this will be just photos,music and some movies, i dont think JBOD or LVM is for me. I canmake the smallest hdd for phots, the next largest for music, and the next largest for movies or something. 

thanks



thanks

Matt

---

### Post by loganfre on 2012-11-02
> **LT72884 said:**
> My wife wants to if you can password protect the netdrive folder so that everytime she double clicks the mapped drive, it asks for a password. she doesnt want others to see her stuff?


Yes, this is the default.


> **LT72884 said:**
> 
She wants to be able to access it from others houses. so i was thinking ssh but she doesnt know how to use command line at all and is used to sites like photobucket. you can see the image before you download it. does ssh have a GUI that can display thumbnails of the contents?

You can use Filezilla to access the server with SFTP (FTP over SSH). Filezilla is not a command line utility, but it doesn't do thumbnails either. Just search for it on google and take a look. Other SFTP clients exits and perhaps one of them will work for you. The other option is to connect to your server via VPN, then all of your services will be available as if the machine was local. That way windows could connect using the normal "Network" tab in Windows Explorer. Windows also has a built in FTP client you could try.

> **LT72884 said:**
> 
Last question, Since i will have 4 IDE drives in the server, and 2 usb drives, does ubuntu read those as seperate drives like windows does? or when ubuntu monts them, they become one giant drive sorta speak? The reason i ask, if i have folders on each drive that need to be accessed, IE, music 1 one ide 1, music 2 on ide 2 etc etc. How do i map those in winxp? same way? //192.168.x.x/music 2 and ubuntu server will know which drive to map it to?
If i remember how FSH works, i can mount the drive anywhere i want to. so for example, everything thing in linux goes under "/" so i can mount all my drives to the same mount point such as /home/matt/netdrive. Will that work or will i have to mount each drive(partition) to its own folder? IE /home/matt/netdrive1,
/home/matt/netdrive2 etc etc? I would like only one folder to show up on the winxp machine. kind of good house keeping. DOnt want to do raid but maybe links or something. symlinks could work i guess.

You can't mount multiple drives to the same point like that. You have to use a drive pooling software such as LVM or Greyhole. With LVM one drive failure = total volume failure. With Greyhole one drive failure = one drive failure. You can mount the drives where ever you want, so you could have one drive at /pictures and another at /videos, etc. That way under windows it would look like several folders on the same drive.

Hope this helps,

Logan

---

### Post by dannyboy79 on 2012-11-02
check out Gallery, its an open source project enabling management and publication of digital photographs and other media through a PHP-enabled web server.

---

