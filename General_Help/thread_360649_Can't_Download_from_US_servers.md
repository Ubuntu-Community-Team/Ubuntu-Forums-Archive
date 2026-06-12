---
title: "Can't Download from US servers"
date: 2007-02-13
forum: General Help
---

### Post by pebkac on 2007-02-13
Hello

I am absolutely not able to download Ubuntu. I am trying to download both the "Alternative" and "Server" discs, since I'm not sure if the server has the "RAID" setup, but I see it's on the alternative one.

I have tried almost all of the servers listed in the "USA" list (I'm located in Canada). I have tried downloading the ISO files via both ftp and http. I can get about 140 MB from the larger alternative file and up to 70 MB from the smaller server file. If I am downloading via HTTP, the message is that the download completed successfully. If I am downloading from an FTP client, I get a message "Connection closed by remote host."

I have logged in to one of the servers via lynx in Linux, the current message there is "Read 140336 of 711562 KB of data, 19 KB/sec (stalled for 7085 sec), ETA 29872"

I even downloaded bittorrent, and the error message I get there in the logs, from any server I try, is "Problem connecting to tracker ([http://torrent.ubuntu.com:6969/announce):](http://torrent.ubuntu.com:6969/announce):) TCPTimedOutError: 10060: Unknown Error."

As you can tell I'm getting a little frustrated. I am behind a firewall, the settings seem OK and I am indeed connecting (since I can seem to get a partial file), but if there is anything I can change on the firewall to make it work, I would appreciate to know.

I have tried on multiple computers on my lan from Windows XP Pro, Windows 2000 and also Linux. I do not know what I am doing wrong, please HELP!!!!  :confused:

---

### Post by igknighted on 2007-02-13
Can you just download the ISO from your windows installs?  Also, are you using http servers or ftp?  I dunno if lynx does ftp or not.  I have used it to download via http many times (haha, gotta love the gentoo install) and it worked fine.  I would try it from a graphical browser, either in windows or linux, and try that.

---

### Post by pebkac on 2007-02-13
> **igknighted said:**
> Can you just download the ISO from your windows installs? 
Not sure what you mean here; I am trying to do just that.

> **igknighted said:**
> Also, are you using http servers or ftp?

All of the above.

I know the original post is lengthy, but if you read it, you will see that I have tried two versions of Windows and one Linux, three protocols, and about 10 servers. I gave the error messages that I received when I tried each one. I also tried both IE and Mozilla. It doesn't seem to make any difference.

---

### Post by igknighted on 2007-02-13
> **pebkac said:**
> Not sure what you mean here; I am trying to do just that.



All of the above.

I know the original post is lengthy, but if you read it, you will see that I have tried two versions of Windows and one Linux, three protocols, and about 10 servers. I gave the error messages that I received when I tried each one. I also tried both IE and Mozilla. It doesn't seem to make any difference.

You could certainly try a european or asian server, but more likely it is a firewall setting.  This I really couldn't help you with not knowing what kind of firewall you are running.

---

### Post by pebkac on 2007-02-13
> **igknighted said:**
> You could certainly try a european or asian server, but more likely it is a firewall setting.  This I really couldn't help you with not knowing what kind of firewall you are running.

I have a custom IPTABLES script running. 

If there is some timeout setting, or a specific port I should unblock, I can do that. However I don't recall there being any timeout settings.

I also run Squid and Squid Guard, but they don't seem to have any timeout settings specified.

---

### Post by pebkac on 2007-02-14
This is getting frustrating.

I still can't download regular CD iso's. I have downloaded and installed TurboFTP, and I noticed that the ISO's under the edgy folder (any server) appear to have shortcut icons and a size of 40 bytes. Therefore when my download gets cut off (every 4-5 minutes), it cannot resume downloading as the ISO and this shortcut file have different file sizes. (UNIX file attributes are lrwxrwxrwx)

I am still getting errors in my BitTorrent client, even though I have opened up a block of ports for it to use in my firewall.

However, I managed to find a REAL ISO file (not a wierd shortcut thing - file attributes are -rw-rw-r--) on a Spanish server, unfortunately it is the ISO for a DVD and it's like 4 GB large. Way more than I need. The good news is, TurboFTP can resume downloads on this file when the FTP connection hangs up (which occurs about every 5 minutes).

QUESTION: does ANYONE know where I can get a REAL iso file, not a shortcut to one. (not a ln file) I reallly want the ISO file for the **CD** version of server and alternate for AMD64. This DVD file is taking forever to download, not to mention I would have to go out and buy a DVD+R to burn it on.

Ubuntu folks: I can't be the only one with this problem! Your mirrors should be set up with directories that have the actual ISO files in them. Not links!!

---

