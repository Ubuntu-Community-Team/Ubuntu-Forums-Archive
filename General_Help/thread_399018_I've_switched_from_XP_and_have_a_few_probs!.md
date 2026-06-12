---
title: "I've switched from XP and have a few probs!"
date: 2007-04-01
forum: General Help
---

### Post by gundo on 2007-04-01
Hello everyone. 
In a bit of a rash moment yesterday I re-partitioned my entire hard disk for use with Ubuntu!
I really like the feel of it and the way it seems so much more 'solid' than XP ever did.
However, I have a few tiny gripes which I am hoping are fixable with a little advice! 
I wasnt sure where to post all this and am not sure if its too much of a tall order but here goes!

1. I have followed the desktop guide and installed all the codecs neccessary to play back DVD's, but the play back seems a bit choppy and the sound to picture sync seems a fraction off. This was never a prob with XP, is this something to do with my settings/drivers? I am using a NVIDIA FX5200 Pci and I used Envy to install the driver.
I also used dvd rip to back up a DVD into an avi file, but when I watch it through any media player on ubuntu there is a fuzzy line across the bottom of the picture. I tried the exact same file on another pc with XP on it and it played back with no lines!! 

2. The in built CD/DVD burner in the file browser doesnt seem to work, every time I try to burn some files it says it failed and to try a lower speed. I have tried using the lowest speed possible and it still fails - however, when I use graveman to burn everything works OK - any thoughts?

3. I used to use uTorrent on XP to download stuff and I would get speeds up to 200K/sec (using 10meg broadband) - the NAT side of things always seemed to sort itself out and the green triangle in the toolbar would come on after a few mins. When I use any bit torrent client in Ubuntu I cant seem to get speeds faster than a few KB/sec - this doesnt seem right?!

4. Are you still here? Thanks! Lastly, web pages dont seem to display correctly with firefox, is this unavoidable? Or  is there a font / patch to make pages display as they would with IE?

I guess you could say that I should have stuck with XP as these are the main things I use my PC for! But even so I think I will stick with Ubuntu as I like the whole open software pricniples and apart from these gripes I love everything else about it - if I can get the above fixed up it would be a very nice bonus!

I hope some of you out there with a bit of time can point me in the right directions!
Thanks very much,
Mark

---

### Post by calraith on 2007-04-01
1. *shrug*

2. I think the file browser uses some sort of packet writing instead of mastering.  Is there an option to format the disc for writing by Nautilus?  (I generally only master CD's and DVD's, as some computers are weird about UDF format as opposed to using Gnomebaker or some other mastering software.)

3. uTorrent supports Universal Plug and Play, which I'm betting your router also supports.  I haven't found a good UPnP torrent app for Linux yet (though I haven't looked terribly hard).  Solution: Define a static port in your BT software, and in your router, forward that port directly to your Linux box.

4. You could try the following:
sudo apt-get install msttcorefonts
... which will install a few Microsoft fonts.  That might help web pages look more like the Windows world.  There are some web pages developed specifically for Internet Explorer, such as Outlook Web Access, and some small business websites where the designer just didn't really care about standards compliance.  Not a whole lot you can do about that.

Although, there is a way to install IE in Linux.  Google ies4linux.  It's traditionally meant only for web designers who want to check compatibility in IE, and not really as a production or default web browser.  Maybe it'll help you though.

Welcome to the community!

---

### Post by gundo on 2007-04-01
Thanks very much for reading and your tips - ill start searching for a Upnp BT client! I cant forward a port as my IP usually changes each day or so!
thanks again,
Mark

---

### Post by calraith on 2007-04-01
If you have a NAT, why can't you configure yourself a static IP?  On my router I can even allocate a static IP based on client MAC address, so I have static IP's even though my machines on my LAN are configured for DHCP.

---

### Post by strabes on 2007-04-02
1) [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) - make sure you have all of the repositories enabled and you have the w32codecs package installed.


2) In order to burn CD's you have to be root. Just use gnomebaker:

```
sudo apt-get install gnomebaker
```

Then once it's installed, run it as root:

```
sudo gnomebaker
```


3) Have you tried azureus or any of the other bittorrent clients for linux? There are many.

4) Could you provide some examples of pages that display "incorrectly" in firefox?

---

### Post by seshomaru samma on 2007-04-02
If your graphic card was installed properly and you still get problems playing media try to play it with VLC
```
sudo aptitude install vlc

```
I find that it plays videos better than other media players

---

### Post by gundo on 2007-04-03
Hi, 
thanks for all of your suggestions.... this is where im up to!

I installed Mplayer and now I have no issues with video playback - so I suppose the problem was rooted in gxine somehow?

I got in touch with Chris who is the creator of qbittorrent, he kindly packaged his client for edgy and ii have installed that ok, I can now get speeds of over 300k which is my best ever yet! I have to forward the port manually (so I guess it will change every few days) but I dont mind doing that. Chris told me that he will be shortly releasing a new version which supports UPnp, so that will be nice.

As for the web pages, my internet banking is a bit funny - entirely useable but just doesnt look as neat and proper as how it was with windows - but Im getting used to it - also Outlook Web access which I use to get my work emails at home - but I guess that figures - again still functional.

As for the CD burning I will try gnomebacker as suggestied when I get home from work!

I have decided that I will probably be sticking with Ubuntu and ditching XP for good! Now I think the only thing I will REALLY miss is Adobe Lightroom - I tried using wine to run this - it installs OK but wont load up - but I can still use it on an old laptop - I suppose you cant have evrything!!!

Thanks again,
Mark

---

### Post by kevpatts on 2007-04-03
You might try 'k3b' also for cd burning. It's a good alternative.

About the IE thing, I think you'll find it's actually the other way round. FireFox displays pages the way they should be displayed and is fully complient with standards, whereas IE ignores standards. Websites that only look good in IE are simply badly written.

FireFox can display websites considerably better than IE, assuming they are complient to W3 standard. For example, go to [www.grack.com](www.grack.com) in both browsers and navigate for a few seconds. This demonstrates the difference in using compliant CSS style sheets only. The difference in browser potential is immediately evident.

---

### Post by 2beers on 2007-04-11
Internet banking:
Normaly uses java - if u use open source java (as often recommended in forums) many java pages look funny... (not amusing though...)
Besides the open source java doesnt support all functions.

So i am using sun's original java - worx fine and pages look the way they are supposed to look.

Opensource java imo looks like linux in general did a couple of years ago - not very pleasing.
Unfortunatly there are still programms out looking that old (i dare say ugly :-)) style.

The original sun java is available via synaptic (universe / multiverse enabled)

BTW:
For me only azureus worx ok on linux - all other BT clients i tried r slow slow and sloooooooooow. If u try azureus (available in synaptic) u may need to use the latest .jar file - available on azureus HP, as there are some bugs - not fixed in the ubuntu sources but allready fixed in the latest available azureus.

---

