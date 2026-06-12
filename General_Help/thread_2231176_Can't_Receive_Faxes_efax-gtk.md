---
title: "Can't Receive Faxes efax-gtk"
date: 2014-06-23
forum: General Help
---

### Post by Ralph L on 2014-06-23
I just reinstalled efax-gtk (along with the modem drivers) in my Ubuntu Precise Pangolin 12.04 (3.2.0-64-generic-pae) system.  I can send faxes fine.  However, I get the following errors, when receiving faxes:

```
efax-0.9a: 17:14:00 opened /dev/modem
efax-0.9a: 17:14:01 using hsfmodem-7.68.00.09oem in class 1
efax-0.9a: 17:14:02 waiting for activity
efax-0.9a: 17:15:21 activity detected
efax-0.9a: 17:15:27 fax call answered
efax-0.9a: 17:15:34 Warning: timed out after waiting
efax-0.9a: 17:15:39 Warning: wrong response after waiting
efax-0.9a: 17:15:39 Error: wrong response after command: +FTH=3
efax-0.9a: 17:15:43 Error: no response after frame data
efax-0.9a: 17:15:45 Error: wrong response after waiting
efax-0.9a: 17:15:27 sent CSI - answering ID
efax-0.9a: 17:15:28 sent DIS - answering capabilities
efax-0.9a: 17:15:34 received DIS - answering capabilities
efax-0.9a: 17:15:34 sent CSI - answering ID
efax-0.9a: 17:15:36 sent DIS - answering capabilities
efax-0.9a: 17:15:39 received DIS - answering capabilities
efax-0.9a: 17:15:43 received UNKNOWN
efax-0.9a: 17:15:43 sent DCN - disconnect
efax-0.9a: 17:15:45 finished - invalid modem response
```

Anybody know what could be wrong??  Hopefully it is a configuration error.

---

### Post by Ralph L on 2014-06-25
I think my problem with efax-gtk was my testing methodology.  I don't have an ordinary telephone line.  I junked Verizon more than a year ago and switched to voice-over-Internet (VOIP) service to save money (only about $3.00 per month for each).  I bought two different VOIP boxes (Ooma and Obihai) and plugged them into my Internet.  So now I have two telephone lines with free calls anywhere in US.  I also use Google Voice to provide voice mail and send free calls.  Anyway for testing, I plugged my printer (which can send faxes) into the Obihai line, and my computer (with efax-gtk on it) into the Ooma line.  I successfully sent a fax from my computer (over Ooma) to the printer (on Obihai line).  However, when I tried to send a fax from the printer to the computer, it didn't work.  I reversed the situation with the computer on the Obihai line and the printer on Ooma.  Still didn't work.

This website suggested testing by having a web site send a fax to myself. ([http://pclosmag.com/html/Issues/201301/page09.html](http://pclosmag.com/html/Issues/201301/page09.html) ).  I did that using this website ([http://faxzero.com/](http://faxzero.com/) ).  This worked with the receiving computer with efax-gtk on either the Obihai line or the Ooma line (it got zero errors on Obihai and one error on Ooma).  So for some reason my computer with efax can send faxes via VOIP and my printer can receive them over the same cable Internet line simultaneously.  However, the reverse is not true.  The printer cannot send a fax and have the computer receive it simultaneously over the same cable Internet line.  Don't know why, but since I will seldom or never want to be simultaneously sending and receiving a fax, I am not going to work on it anymore.  

Anyway efax-gtk and the updated soft-modem driver that Ganton tells how to make ([http://ubuntuforums.org/showthread.php?t=1903439&highlight=ganton](http://ubuntuforums.org/showthread.php?t=1903439&highlight=ganton) ) work fine on Precise Pangolin 12.04 3.2.0-64-generic-pae.

Note:  If anybody else decides to use Ganton's method, when it come to doing "sudo make install" and "sudo hsfconfig", change it to:
```
sudo -s
make install
hsfconfig
exit
```
Otherwise you get permission errors.  Apparently sudo doesn't always give you permission to all files.  I don't know why that is, but I have had the problem before and the use of "sudo -s" solves it.

Maybe this post will be useful to somebody else who also lives in the past, still has a modem on their computer, and wants to use it to log into the Internet or send and receive faxes.

---

