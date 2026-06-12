---
title: "Installed Gran Paradiso  and I do not know where it went."
date: 2007-04-30
forum: General Help
---

### Post by El Viejo Lobo on 2007-04-30
I have feisty Fawn in my box, the one I have for learning and adventure experiments. 
I think that I installed Gran Paradiso Firefox 3, at least I followed the How to:
[http://www.mozilla.org/projects/firefox/3.0a3/releasenotes/](http://www.mozilla.org/projects/firefox/3.0a3/releasenotes/)
 tar -xjvf granparadiso-alpha3.tar.bz2
cd firefox
./firefox

After the command './firefox' I got my Firefox -that was open blinking or fading for a second and then came back as normal as it was before.
Do I have the new version installed or not? how can I check it?
Thanks.

---

### Post by llamakc on 2007-04-30
Click HELP | ABOUT MOZILLA FIREFOX

---

### Post by kerry_s on 2007-04-30
Yes and no, with that command you have it in your home account and your running it from there. You can keep that setup if you want to run it from your home, but you want to link it to /usr/bin, so when ever something calls firefox it calls the 1 you want.

sudo rm /usr/bin/firefox
sudo ln -s /home/you/firefox/firefox /usr/bin/firefox

also

sudo rm /usr/bin/mozilla
sudo rm /usr/bin/mozilla-firefox

sudo ln -s /usr/bin/firefox /usr/bin/mozilla
sudo ln -s /usr/bin/firefox /usr/bin/mozilla-firefox

---

### Post by kerry_s on 2007-04-30
Oh, by the way it's up to alpha4 already.-> [http://developer.mozilla.org/devnews/index.php/2007/04/27/gran-paradiso-alpha-4-now-available-for-download/](http://developer.mozilla.org/devnews/index.php/2007/04/27/gran-paradiso-alpha-4-now-available-for-download/)

Man, that sucks almost all my extensions don't work. Plus it's alot slower.

---

### Post by El Viejo Lobo on 2007-04-30
> **kerry_s said:**
> Yes and no, with that command you have it in your home account and your running it from there. You can keep that setup if you want to run it from your home, but you want to link it to /usr/bin, so when ever something calls firefox it calls the 1 you want.

sudo rm /usr/bin/firefox
sudo ln -s /home/you/firefox/firefox /usr/bin/firefox

also

sudo rm /usr/bin/mozilla
sudo rm /usr/bin/mozilla-firefox

sudo ln -s /usr/bin/firefox /usr/bin/mozilla
sudo ln -s /usr/bin/firefox /usr/bin/mozilla-firefox

It looks like I do not have it, noting happened after terminal got the above commands.
Can I make it work paralel to Firefox 2 that came with Feisty?:confused:
  
[COLOR="Red"]**After closing the Firefox 2 I could not open it again, made complete uninstall and new install with Synaptic, Firefox 2 is OK  with all bookmarks as it was.  Is the adventure worth keep trying to get "gran Paradiso"? **[/COLOR]

---

### Post by El Viejo Lobo on 2007-04-30
> **kerry_s said:**
> Oh, by the way it's up to alpha4 already.-> [http://developer.mozilla.org/devnews/index.php/2007/04/27/gran-paradiso-alpha-4-now-available-for-download/](http://developer.mozilla.org/devnews/index.php/2007/04/27/gran-paradiso-alpha-4-now-available-for-download/)

Man, that sucks almost all my extensions don't work. Plus it's alot slower.


May be it's better to wait for the release of the beta?

---

### Post by llamakc on 2007-04-30
Or install it into /opt and create a desktop shortcut specifically for THAT version.

---

### Post by kerry_s on 2007-04-30
I've already deleted it i just wanted to see where it was at, not worth it to me.

---

