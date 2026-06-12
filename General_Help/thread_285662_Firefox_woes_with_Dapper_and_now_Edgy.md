---
title: "Firefox woes with Dapper and now Edgy"
date: 2006-10-27
forum: General Help
---

### Post by tonedog on 2006-10-27
It is probably worth mentioning that I am essentially totally new to Ubuntu/Linux.  My problem is that several of the sites that I tend to visit somewhat frequently do not display properly in Firefox on Ubuntu.  I say on Ubuntu b/c they do display with Firefox in Windows.  The two sites in question tho they are not the only ones i have had issues with are:
[http://www.nbc.com/](http://www.nbc.com/) 
and various subsites of [http://www.scifi.com/](http://www.scifi.com/) (like [http://www.scifi.com/battlestar/](http://www.scifi.com/battlestar/))

The NBC site doesn't appear to load completely and the rollover navigators at the top appear behind the other stuff on the site instead of in front of it.

For Battlestar Galactica it appears that the site is loading then the whole page goes white except for 2 adds for Microsoft Visual Studio 2005.

Now as I have said I am a newbie to Linux/Ubuntu so hopefully there is just something I need to tweak to get this to work right.  I had hoped that installing Edgy (and the included upgrade to Firefox 2) would resolve the issue but that does not appear to have happened.

Thanks,
Tony

---

### Post by tronica on 2006-10-27
make sure you have flash installed

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

and you could try which i have done, is to install flash 9 beta, i have had no problems with it, but keep in mind it is beta.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_update_to_Flash_Player_9_Beta_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by tonedog on 2006-10-27
Well i thought I had previously installed but I must have messed something up when I installed it.  I followed your links and I actually went ahead and setup and ran automatix2, part of which should have installed flash and now the scifi pages appear to work.  However, the menu's on nbc still don't appear to be working.

---

### Post by timberline5 on 2006-10-27
What solved some problems for me in firefox was with ipv6

what you do is, in firefox type into the Url box "about:config" (without quotes) filter "ipv6"
make sure that the value is set to "true"

good luck

---

