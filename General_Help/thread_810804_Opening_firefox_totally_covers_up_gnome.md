---
title: "Opening firefox totally covers up gnome"
date: 2008-05-28
forum: General Help
---

### Post by watupgroupie on 2008-05-28
Okay, I was using firefox and other apps. I folded the laptop up, ate lunch. I came back and launched firefox and now it is totally covering up gnome. This is only happening on firefox and I'm running the latest version of ubuntu. So I have no bottom panel and no top panel, the close, maxamize and minimize buttons are gone as well. The only way I can manage to get back is by clicking on the panel where the file, edit, view,etc buttons are and clicking customize. It brings up gnome again for some reason. I can also go file--exit obviosly too. What can I do?

---

### Post by FuturePilot on 2008-05-28
That happened to me once. I have no clue why it was doing that. But creating a new Firefox profile fixed it.
```
mv ~/.mozilla ~/.mozilla_old
```
Make sure you shutdown Firefox before running that command or else it won't work. Afterwards if that fixes it and you want your bookmarks back, open your Home folder and press Ctrl+H to show hidden files and find the .mozilla_old folder. Open that and go into the profile folder. Usually has a bunch of random numbers and letters followed by .default. In there you will find your bookmarks.html file. You can just copy that over to your new profile in the new .mozilla folder. Make sure you have Firefox closed before doing that.

---

### Post by kebes on 2008-05-28
> **watupgroupie said:**
> firefox [...] is totally covering up gnome. This is only happening on firefox and I'm running the latest version of ubuntu.

Did you perhaps just accidentally switch Firefox into "fullscreen" mode? Try pressing F11 to toggle between fullscreen and normal mode.

---

### Post by watupgroupie on 2008-05-28
Thanx FuturePilot that fixed it and I didn't lose my history or bookmarks either. Kebes it wasn't just fullscreen either, it looked diffrent than that. Thank you anyway. Speedy reply too, thank you very much :D

---

### Post by bakul on 2008-12-05
I had the same problem and what I did was to simply close all the firefox windows and delete the .mozilla folder from Home. Then I started the Firefox again and it was fine! Of course I copied the Extensions folder before deleting so that I could retain my favorite add-ons- I just pasted the contents of that folders within the new Extensions folder.

Another temporary solution worked, just hit F11 twice!

---

### Post by Viranh on 2009-03-21
I just had this happen to me today randomly. I can confirm that it is NOT fullscreen. However, to temporarily fix it, if I go to fullscreen I can hit the maximize/minimize button and it goes back to normal. It still opens the weird way if I open a new firefox though. I wish I knew why. It is extremely annoying.

---

### Post by oujgazoiro on 2009-03-27
I've got the same problem. It's not fullscreen, there's still a menubar but no windowbar and no system panel. Removing my .mozilla folder did work, but I don't want to loose all my bookmarks and extensions. Copying the bookmarks.html into the new .mozilla folder didn't restore my bookmarks. 
I think I'll be using F11 until a patch fixes this problem...

---

### Post by Confuseling on 2009-03-27
Try System -> Preferences -> CompizConfig -> Workarounds -> Legacy Fullscreen support (off)

---

### Post by oujgazoiro on 2009-03-27
I don't have no CompizConfig under Preferences... I'm using Ubuntu 8.10 by the way...

---

### Post by rjl6591 on 2009-03-27
Not sure about 8.10, but in 8.04 it's System->Preferences->Advanced Desktop Effects Settings->Utility->Workarounds

---

### Post by oujgazoiro on 2009-03-28
Does anybody of you having the same problem play hattrick? ([http://www.hattrick.org]("http://www.hattrick.org")) Today I updated the Foxtrick plugin for Firefox and the problem with firefox is solved, as it seems...

---

### Post by Toady00 on 2009-04-18
It just happened to me. I closed my laptop for a few and when I opened it back its not in fullscreen but covering up the panel like everyone already said.

---

### Post by warpasylum on 2009-05-02
I've got the same problem here.  Hitting F11 twice works to get it back to normal.  Not sure what's cuasing the issue though, never had this happen before. Ougazoiro, you might want to try installing Advanced Desktop Effects Settings (ccsm) via Synaptic. I didn't think I had Compiz either. Turns out I did, I just didn't have the settings manager installed. I'm also running Intrepid.

---

### Post by DeMus on 2009-05-02
> **oujgazoiro said:**
> I've got the same problem. It's not fullscreen, there's still a menubar but no windowbar and no system panel. Removing my .mozilla folder did work, but I don't want to loose all my bookmarks and extensions. Copying the bookmarks.html into the new .mozilla folder didn't restore my bookmarks. 
I think I'll be using F11 until a patch fixes this problem...

No, you won't restore your bookmarks by copying the file bookmarks.html since FF does not use this file. Starting with version 3.0 it uses a different file, namely places.sqlite. You can however export your bookmarks using menu Bookmarks - Organize Bookmarks and choosing Import-Export.

---

### Post by warpasylum on 2009-05-04
Hey guys. Thanks so much. System -> Preferences -> Compiz Config -> Workarounds -> Legacy Fullscreen Support (off) worked perfectly for me. Firefox is behaving again. :P

---

### Post by cfree220 on 2009-05-04
This post was helpful for me. Turning off legacy fullscreen support solved the problem, without me having to move around the ~/.mozilla folder. Note, however, that this may cause window problems with other applications. I believe the the remote desktop viewer requires LFS to be enabled in order to properly fullscreen (else you will not be able to minimize the window or exit fullscreen).

---

### Post by Darth Buh on 2009-05-18
I'm using Ubuntu 8.10, and had the same issue.

To correct the issue, I had to install the "compizconfig-settings-manager" package, and the pathway to fix that was opened up was Preferences -> CompizConfig Settings Manager -> Utility -> Workarounds.  Seems the package was not part of the default operating system installation.

Fixed the problem for me.

DB

---

