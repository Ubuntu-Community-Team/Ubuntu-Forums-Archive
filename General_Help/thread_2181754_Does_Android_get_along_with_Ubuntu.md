---
title: "Does Android get along with Ubuntu?"
date: 2013-10-18
forum: General Help
---

### Post by MagisterDixit on 2013-10-18
I am finally joining the smartphone movement and I have one question: Does Android work well with Ubuntu? By that I mean, can I backup my purchases and can I easily sync music that is on my PC with my phone. I already know that Ubuntu will not work with iTunes or any newer Apple devices. So if I get a Galaxy S4, will I be able to do what I want without jumping through hoops or resorting to my wife's horrid Windows PC? Keep in mind that the easy transfer of my music is my primary concern. And is there a particular music app I would need to be using? Right now all my music is in Rythmbox. Thanks for the help!

---

### Post by SeijiSensei on 2013-10-18
Current Android devices use the Media Transfer Protocol to exchange files with other systems.  Support for MTP was less than stellar in versions of Ubuntu before 13.04.  Starting with that version, you can simply plug the phone into your computer with the USB cable, and it will appear as a storage device.  Any music files you copy into the Music folder will then be available.  

I also recommend [Cover Art Downloader](https://play.google.com/store/apps/details?id=com.birbeck.android.coverart&hl=en) to find missing album covers.  It even found the covers for some Japanese anime CDs and jazz albums from the 50's and 60's.

I added a MicroSD card to my Galaxy S3 and created a Music folder there which the apps find without any extra effort on my part.  The standard player supports less common formats like Ogg Vorbis and FLAC, too.

If you want to watch video files, I recommend [MX Player]("https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad&hl=en") which supports a wide variety of formats and subtitles.  It also plays videos encoded in the Hi10P format, which the standard video player does not.

I also use [JuiceSSH]("https://play.google.com/store/apps/details?id=com.sonelli.juicessh&hl=en") for times when I need to log into a server.

One thing you won't be able to do is mount remote file systems using NFS or Samba.  Unless you root your phone, you cannot create arbitrary mount points in the filesystem.  There are SMB clients that you can use to access a file share; I use [AndSMB]("https://play.google.com/store/apps/details?id=lysesoft.andsmb&hl=en").  I also have used an app called [WiFi File Transfer]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer&hl=en") that turns the phone into a webserver.  I used that to transfer files before upgrading to 13.04.  The free version has a limitation on the size of uploaded files, so I spent the $3 to get the "Pro" version.

---

### Post by MagisterDixit on 2013-10-18
I'm still using Ubuntu 12.04 LTS. You say the MTP wasn't as good before 13.04. Should this concern me? Will it be a real problem? I use my computer for home and work and am really not interested in upgrading unless it's to another LTS which won't be out untill 14.

---

### Post by SeijiSensei on 2013-10-18
MTP really didn't not work cleanly for me in 12.04, but I use Kubuntu which has its own method for handling external devices ("kio-slaves").  It might work better on vanilla 12.04, but I cannot say.  The SMB and wifi methods worked fine with 12.04, but depending on your wireless network speeds they will likely be slower than a USB connection.

Kubuntu 13.04, and now 13.10, are clear improvements over 12.04LTS and show no instabilities.  Again I cannot say whether this is true for Ubuntu, but comments I have read here suggest 13.04 is a worthwhiile upgrade even though it is not an LTS version.  It will certainly be supported through next April when 14.04LTS will be released.

---

### Post by MagisterDixit on 2013-10-18
Thanks, SeijiSensei! I will probably try to keep 12.04 just because I am still a noob and the risk of user error is high. But if I get an Android and it just won't work, I'll know what to do!

---

