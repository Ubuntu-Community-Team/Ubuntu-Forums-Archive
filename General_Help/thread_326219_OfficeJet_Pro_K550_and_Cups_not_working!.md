---
title: "OfficeJet Pro K550 and Cups not working!"
date: 2006-12-27
forum: General Help
---

### Post by Flavian on 2006-12-27
Hi guys! I got the following problem, I have a new printer and I don't get it to work. I searched the forums, there seam to be people that have it up and running with Cups, but mine doesn't.
I can't find the printer in the network, it just doesn't show up.
And I am quiet a newbie so I don't even know what to put in the ipp:// line :(

The weird thing is also that I can NOT access: [http://localhost:631](http://localhost:631) it just doesn't load and then after a while my browser says, "Error, couldn't connect to remote server".
It worked before though, I know, because I set up another printer that way already!!

I would be glad for any advice :)
Thanks
Flo

---

### Post by Soarer on 2006-12-27
It should be easy, but you will need to know the IP address of the printer (which is what you have to put in IPP:// line).

[This thread]("http://www.ubuntuforums.org/showthread.php?t=274466") might help.

According to [LinuxPrinting]("http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_Pro_K550") it should work 'perfectly'.

On my Office 7300, you can set an IP address on the printer itself. I don't know how you do it on the 550, but your documentation or HP's website should tell you.

Good luck, but once you have the IP address sorted the rest is easy with HPs :)

---

### Post by Flavian on 2006-12-27
Okay I got that with the IP.
But still I think there's something wrong with CUPS!
It takes a LOT of time to load the "printing-database" at the beginning and now I try to print, the processor goes up to a 100% maximum and it just does not print. I can't even klick on the priner symbol in the taskbar. :(
And  [http://localhost:631](http://localhost:631) is still not accessible!

---

### Post by Flavian on 2006-12-27
Help?

---

### Post by Soarer on 2006-12-28
OK - not to worry - we'll get there :)

For my HP7310 I use HPJetDirect as the method, not CUPS. In System>Admin>Printing double-click on 'New Printer' , then 'Network Printer' then select 'HP JetDirect' from the drop down list (which normally displays 'CUPS' - HPJetDirect is at the bottom of the list).  Type the IP address of your printer into the 'Host' field. 'Forward'.

Choose 'HP' from the drop down and your printer (K550?) from the next list. Use the suggested hpjis driver (do not change it, in other words)  'Forward'

Give the printer a name, and location if you like, 'Apply'

That should work - it does on mine as I have just done it twice :)

---

### Post by Flavian on 2006-12-28
*lol* I am an idiot!
Why didn't I try this before?? - I thought I did and it didn't work, and so I stuck with Cups not trying HP JetDirect.
Man you saved my day ;) *lol* so easy... shame on me.

Thanks for your help, works like a charm.
God bless you
Flo

---

### Post by Soarer on 2006-12-29
Great news Flo - I'm glad you got it working. Thanks for posting that it worked for you. 

I installed my HP 7310 on Windows as well as Ubuntu - had to load several megs of software over about 1/2 hour. Ubuntu is so much easier :)

By the way, you should now be able to administer your printer by typing its IP address in you browser. Mine can anyway :)

---

