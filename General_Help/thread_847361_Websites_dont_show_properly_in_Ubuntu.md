---
title: "Websites dont show properly in Ubuntu"
date: 2008-07-02
forum: General Help
---

### Post by iheartubuntu on 2008-07-02
Ive attached two images as an example.

I normally use Firefox (2.x & now 3.0) and have also tried the newest Opera and Epiphany browsers. I get the same problem. When trying to see menus that come down on a website, like on MLB or MLSnet (and many others) the menu is BEHIND any java stuff. This is a major bug. I dont have this problem with XP systems, but dont use them anymore, so.... here I am. I havent checked other distros like suse or debian so I cant comment, but this problem seems to so far be with Ubuntu/linux. I also noticed this when I had 7.04 and 7.10.

Check it out... (any fixes? thanks!)....

[IMG]http://www.shirtees.net/mlb-error.jpg[/IMG]

[IMG]http://www.shirtees.net/mls-error.jpg[/IMG]

---

### Post by iheartubuntu on 2008-07-02
* bump *

thanks anyone!

---

### Post by Pablo89 on 2008-07-02
Maybe a font problem? Does installing the 'msttcorefonts' restricted package help? I don't know if it is legal at you, but some webdevs may ignore the fact that some people don't have Microsoft's fonts...

---

### Post by nikgare on 2008-07-02
You need to ask Adobe.
This is due to a very long standing bug in Flash which Adobe seem either unwilling to or not able to fix.

---

### Post by iheartubuntu on 2008-07-02
I'll check the msttcorefonts right now.

In the mean time, can everyone reading this check these websites and check the menu bar and see if the pulldown menus drop behind the java stuff? Thanks!

[http://www.mlsnet.com/](http://www.mlsnet.com/)

[http://www.mlb.com/](http://www.mlb.com/)

---

### Post by rossjman1 on 2008-07-02
Seems to be fine for me. Do you have flashplugin-nonfree installed?

---

### Post by iheartubuntu on 2008-07-02
I know when I installed flash, I picked Adobe as my option. How can I go about changing that?

---

### Post by iheartubuntu on 2008-07-02
> **rossjman1 said:**
> Seems to be fine for me. Do you have flashplugin-nonfree installed?

Yah, I do have that.

---

### Post by goforlinux on 2008-07-02
Sounds like a flash player problem and sometimes some websites very rare but it happebns need IE to open them. But sounds like another glitchy adobe problem.....

---

### Post by iheartubuntu on 2008-07-02
Should I try Gnash?

EDIT: I uninstalled flash and installed gnash... nothing changed.

---

### Post by fragos on 2008-07-02
Site coded with IE proprietary markup or worse yet Active-X instead of Javascript. Won't work properly. Fonts can alsa be a problem. Arial Narrow for example which doesn't have a close alternate. A well coded site should list in order it's font preferences and therefore substitutions to insure the best compatibility across platforms. Vista has new versions of font with new names which makes matters more complex. The real villians here are Microsoft and web developers that use Microsoft tools and don't test for compatibilty with multiple platforms. I develop site with standard markup and avoid those markups not properly handled by IE.

---

### Post by Doji on 2008-07-02
I have this problem as well, and since it exists on [Revision3]("http://revision3.com/systm/supercooling/") I'm reluctant to blame it on poor coding standards. If anyone has a fix, I'm all ears.

---

### Post by jamesstansell on 2008-07-03
Installing the flashblock firefox extension lets the menus show up - until you let the flash content play.  So probably not a very helpful workaround.

---

### Post by yaknowwat on 2008-07-03
Yes this is an issue with flash plugin which i can thankfully say will be fixed in flash player 10.

There is the Beta 2 which came out today that addresses this issue if you would like to get it here is a link.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

The easy way to install this is to install flash player 9 then drop the new libflashplayer.so (you can find it be extracting the TAR.GZ ) file over the older one.

the libflashplayer.so file is kept in.

/usr/lib/flashplugin-nonfree/

you could do it all terminal if you wished by copy pasting and using these commands.

```

sudo apt-get install flashplugin-nonfree
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz
tar -xzvf ./flashplayer10_install_linux_070208.tar.gz
cd ./install_flash_player_10_linux
sudo mv './libflashplayer.so' '/usr/lib/flashplugin-nonfree/'

```

---

### Post by SuperMike on 2009-10-15
I think the wget statement needs to pull the file from here:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

---

### Post by phillw on 2009-10-15
> **fragos said:**
> Site coded with IE proprietary markup or worse yet Active-X instead of Javascript. Won't work properly. Fonts can alsa be a problem. Arial Narrow for example which doesn't have a close alternate. A well coded site should list in order it's font preferences and therefore substitutions to insure the best compatibility across platforms. Vista has new versions of font with new names which makes matters more complex. The real villians here are Microsoft and web developers that use Microsoft tools and don't test for compatibilty with multiple platforms. I develop site with standard markup and avoid those markups not properly handled by IE.

I'm with you 100% on that one !! - Although the sites indicated did run on my set-up, once I'd told NoScript to temporarily allow the site.

I also code to xhtml, strict - It's been 'fun' learning just how strict, STRICT is !!!

Oh, and by the way ....

[http://web.mlsnet.com/index.jsp](http://web.mlsnet.com/index.jsp)

When checked against W3C standards, says it is using xhtml, transitional ...
It returns          733 Errors, 134 warning(s)       When checked - So, before you go blaming your browser / flash / kitchen sink - Maybe a little note to the website author asking them to comply with standards that they claim to - would go a long way to help :)

Phill.
P.S. Their Style Sheet doesn't fare much better ....
**Sorry! We found the following errors (36)**

---

### Post by fragos on 2009-10-15
> **phillw said:**
> I'm with you 100% on that one !! - Although the sites indicated did run on my set-up, once I'd told NoScript to temporarily allow the site.

I also code to xhtml, strict - It's been 'fun' learning just how strict, STRICT is !!!

Oh, and by the way ....

[http://web.mlsnet.com/index.jsp](http://web.mlsnet.com/index.jsp)

When checked against W3C standards, says it is using xhtml, transitional ...
It returns          733 Errors, 134 warning(s)       When checked - So, before you go blaming your browser / flash / kitchen sink - Maybe a little note to the website author asking them to comply with standards that they claim to - would go a long way to help :)

Phill.
P.S. Their Style Sheet doesn't fare much better ....
**Sorry! We found the following errors (36)**

The Opera browser people did a study and found that only 4% of sites pass the W3C checks without a problem. I use the W3C checks as one of my sales tools when proposing a new site to a client.

---

