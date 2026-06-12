---
title: "Shared printing issue"
date: 2017-02-10
forum: General Help
---

### Post by MrGibbage on 2017-02-10
I have a Brother HL-340CN networked color laser printer. I have a Win10 box that can print directly to it, and I have a Ubuntu 16.04 box that can also print directly to it. I have enabled sharing in cupsd.conf (listen *:631 and restarted cupsd). I then added the printer in my Win10 box by browsing to the Ubuntu box and selecting the shared printer. It showed up and everything looked great. But when I go to print the test page, no error messages show up on either box, and I don't see anything in the print queue on either box. And of course nothing prints. Not sure where to start troubleshooting this mostly because it is really hard to google for this exact scenario. I am deliberately not attaching any files because I don't know what files would be interesting here. 

To recap: The printer works when added directly to both the Win10 and Ubuntu box. It shows up in the network share explorer on the Win10. I can add the printer "through" the Ubuntu box when browsing the network shares from the Win10 box. But I can't print to it. This tells me that the sharing is set up correctly, but something else is broken.

By the way, the reason I want to do this is because I am trying to set up airprinting for my daughter's ipad, and I know if I can't get shared printing working through windows, then it won't work with the ipad either.

Let me know what files need to be attached and I'll post them.

Thanks in advance!

---

### Post by ajgreeny on 2017-02-11
I do not share a printer in the way you do but I am wondering if the bug raised for cups at [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1598300) may have something to do with your problem.

It seems that cups will keep stopping in 16.04 resulting in any activity or printing that depends upon cups failing. You may be able to overcome this problem by enabling the proposed repositories in software-sources ->Developer Options tab, upgrading just cups from2.1.3-4 to 2.1.3-4ubuntu0.1, along with the dependencies, then quickly disabling the proposed repos again as they are a bit too risky to keep enabled all the time.

I did that in January and have had no problem accessing localhost:631 since that, though previously I had to keep restarting cups in order to access that address.

---

### Post by SeijiSensei on 2017-02-11
I have an Android phone with the Brother app installed.  It can print directly to my networked printer without needing any intermediary server. A quick search tells me there is an equivalent [app for Apple devices]("https://itunes.apple.com/us/app/brother-iprint-scan/id382775642?mt=8").  Have you/she tried that approach?

---

### Post by MrGibbage on 2017-02-11
@ajgreeny, thanks. I am not sure if that is the same issue or not. Could be.

@SeijiSensei, I had not seen that app! If that works, that will definitely be a better way to do this. I'll get her to install it this afternoon. Thanks for the tip in any case :)

---

### Post by MrGibbage on 2017-02-13
*sigh* The Brother iPrint app doesn't work for me. I guess the 3040CN printer is not supported by the app. 
[http://www.brother-usa.com/connect/mobile/ios/color-laser-led/](http://www.brother-usa.com/connect/mobile/ios/color-laser-led/)

I even tried it from my android tablet with negative results. :)

Anyone else have any ideas for what may be going wrong here with workarounds I can try?

---

### Post by SeijiSensei on 2017-02-13
Does the printer have a [static IP address]("https://www.manualslib.com/manual/355717/Brother-Hl-3040cn.html?page=118")?  I assigned my HL-3170CDW a static address so that all my devices know where it is.  Any server or server-like device should have a static address.  And you are using wifi on your iThings, right, so that they and the printer are on the same network? 

I really doubt that the Brother app won't work with your printer since all Brother devices share the same set of printing commands.  I'm guessing it's a configuration issue of some sort.

---

### Post by MrGibbage on 2017-02-13
Yes the printer has a static IP address. I printed the system info page from the printer menu and verified this. Every option is enabled except IPv6. Yes, we are all using wifi on the same network. Not messing with portforwarding for now.

Thanks for replying though! :) :)

---

