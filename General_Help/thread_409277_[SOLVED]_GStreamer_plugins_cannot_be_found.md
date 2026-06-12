---
title: "[SOLVED] GStreamer plugins cannot be found"
date: 2007-04-14
forum: General Help
---

### Post by Cariboo1938 on 2007-04-14
Hi all,
Since my last system update on April 12, 2007 I have problems using 'Rhythmbox Music Player'. If try to play a music file I get the message:
> The GStreamer plugins to decode "MP3" files cannot be found
Can somebody tell me what I have to do, please?:confused:

---

### Post by bapoumba on 2007-04-14
Hi,
did it use to work?
This [link]("https://help.ubuntu.com/community/RestrictedFormats/MP3") can help you. Please post again if it does not.

---

### Post by Cariboo1938 on 2007-04-14
> **bapoumba said:**
> Hi,
did it use to work?
This [link]("https://help.ubuntu.com/community/RestrictedFormats/MP3") can help you. Please post again if it does not.
Yes it always did. Thanks for the link but it only talks about Ubuntu Dapper and Amarock/Kubuntu. I'm running Edgy Ubuntu 6.10_amd64 and I wanted to use Rhythmbox Musicplayer, because I haven't installed any KDE programs yet. I don't want to convert MP3 to Ogg either. What else can I do?

---

### Post by bapoumba on 2007-04-14
Make sure you have these installed:
```
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```
Not all of them are for playing MP3, I did not sort them out from [here]("https://help.ubuntu.com/community/RestrictedFormats").
Universe and multiverse repositories should be enabled.

Could you also start rhythmbox from a terminal (> Accessories > Terminal > run "rhythmbox" without the "") and paste any error playing MP3.

---

### Post by Cariboo1938 on 2007-04-14
> **bapoumba said:**
> Make sure you have these installed:
```
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```
Not all of them are for playing MP3, I did not sort them out from [here]("https://help.ubuntu.com/community/RestrictedFormats").
Universe and multiverse repositories should be enabled.

Could you also start rhythmbox from a terminal (> Accessories > Terminal > run "rhythmbox" without the "") and paste any error playing MP3.No, I have none of them installed. I'll do this later.
For now, here is the terminal message:
> karibu@BitByters-Desktop:~$ sudo rhythmbox
Password:

(rhythmbox:10809): Rhythmbox-WARNING **: couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:10809): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

(rhythmbox:10809): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

(rhythmbox:10809): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running
karibu@BitByters-Desktop:~$ 

---

### Post by Cariboo1938 on 2007-04-14
Thanks to 'bapoumba'!

the missing packages responsible for my case were

> gstreamer0.10-ffmpeg, gstreamer0.10-plugins-ugly  

After installing these packages Rhythmbox works again! I still get the Rhythmbox-Warnings
> karibu@BitByters-Desktop:~$ sudo rhythmbox

(rhythmbox:32096): Rhythmbox-WARNING **: couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:32096): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

(rhythmbox:32096): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:32096): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running
karibu@BitByters-Desktop:~$ 
and I don't know if this of any interest for the developers?

---

### Post by WinstonSmith on 2007-05-27
> **Cariboo1938 said:**
> Hi all,
Since my last system update on April 12, 2007 I have problems using 'Rhythmbox Music Player'. If try to play a music file I get the message:

Can somebody tell me what I have to do, please?:confused:

Unfortunately, that is a known bug:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg92468.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg92468.html)

---

