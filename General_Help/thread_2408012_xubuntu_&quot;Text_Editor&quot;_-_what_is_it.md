---
title: "xubuntu &quot;Text Editor&quot; - what is it?"
date: 2018-12-12
forum: General Help
---

### Post by lou6 on 2018-12-12
Yesterday (12/11/18) software updater notified me of a pending upgrade so I went ahead with the installation.  Since then I ad unable to open .txt files with mousepad (the default app) and there is a new entry in the list of recommended applications (Text Editor) that does not seem to be an application - it does not appear in the whisker menu 'all' list and it does not exist in synaptic.  Double-clicking a text file just causes a spinning icon when it used to just open with mousepad.  The really strange thing is that a desktop shortcut to a .txt file that I use to jot down notes opens normally with mousepad.

Does anyone know what this "upgrade" was and why it's causing these annoying effects?

Thanks in advance for any explanation...

---

### Post by Dennis N on 2018-12-12
Text Editor is just the descriptive name (akin to Web Browser) and can be changed by the user. To see what application this was, look at the history log for that transaction at:
**/var/log/apt/history.log**

---

### Post by lou6 on 2018-12-12
Thanks for replying - I checked history log and it doesn't really tell me much.  How would I go about changing the app referred to by the descriptive name "Text Editor"?  I've looked at preferred applications in xubuntu settings but text editor is not there.

Prior to the above-mentioned "upgrade" mousepad was the default application for text files - now that no longer works.

---

### Post by HermanAB on 2018-12-12
I think it is leafpad.

Run top, then launch the editor.

...or run the editor and click Help, About or some such.

---

### Post by slickymaster on 2018-12-12
Xubuntu is still shipping Mousepad as the default text editor and there haven't been any discussions, so far, regarding changing it.

---

### Post by lou6 on 2018-12-12
Text Editor is apparently opening gedit but with Text Editor set as default application text files still do not open with double-click, the clock thingy just spins and spins.  The only way this works is to open Text Editor from the Whisker Menu (which calls gedit) and doing a second open of the file I need from there.

Or, as mentioned above, create a desktop link to the file I need and click that link to open (with preferred app set to mousepad).

Makes no sense at all (plus no way to choose app for Text Editor as I can for Web Browser in Xubuntu settings).

I'm confused - everything was working just great before the 12/11/18 "upgrade"...

---

### Post by Dennis N on 2018-12-12
> Text Editor is apparently opening gedit
I looked at my Xubuntu 18.04 and there have been no updates to mousepad this month. gedit doesn't belong to Xubuntu - it's intended for Ubuntu (Gnome Desktop). Did you install gedit yourself, or perhaps you installed XFCE desktop to Ubuntu? That would account for it's presence.

You might uninstall gedit.

_Tip:_
To see applications registered to open plain text files, you can run in terminal:
```
cat /usr/share/applications/mimeinfo.cache | grep text/plain
```
(This is the same list of applications you see when you use right-click > open with)

---

### Post by lou6 on 2018-12-12
I haven't installed gedit but when I click Text Editor from the Whisker Menu gedit is what opens.  If Text Editor is indeed a descriptive name then Xubuntu setting should allow for configuring it as I can for File Manager or Terminal Emulator.

I installed Xubuntu from scratch when 18.04.1 became available so no, I did not graft xfce over gnome. 

I guess I'll remain confused and work around whatever happens.

Thanks for the replies - I won't mark this as solved just yet...

---

### Post by Dennis N on 2018-12-12
> I installed Xubuntu from scratch when 18.04.1 became available
Same here, but it doesn't install gedit. It could have been installed in as a dependency of another application, I suppose.
_What is in the default installation:_
[http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/xubuntu-18.04.1-desktop-amd64.manifest](http://cdimage.ubuntu.com/xubuntu/releases/18.04.1/release/xubuntu-18.04.1-desktop-amd64.manifest)
No gedit.

I would remove gedit and see if that fixes the problem. Some internal conflict perhaps?

_Tip:_

If you want a text editor based on gedit but designed for any environment, install **xed** instead. It (along with several others, collectively called xapps) was developed by Linux Mint to be distro neutral, and blend in with your theme. I installed it to supplement mousepad in Xubuntu, and also have it on Lubuntu LXDE. It's not in the Ubuntu 18.04 repositories, but there is a PPA:

[https://launchpad.net/~embrosyn/+archive/ubuntu/xapps](https://launchpad.net/~embrosyn/+archive/ubuntu/xapps)

---

### Post by CatKiller on 2018-12-12
> **lou6 said:**
> I guess I'll remain confused and work around whatever happens.

"Text Editor" (in multiple languages) is how gedit is described in its .desktop file.

It sounds like you've pulled in gedit as a dependency when you've installed something else and it's tried and failed to set itself as the default application for text files (potentially because you aren't using all the other Gnome framework bits).

I'd just uninstall it. It'll either simply go away, or try to also remove whatever it was that pulled it in so you can decide.

---

### Post by dragonfly41 on 2018-12-12
Running this command ..

```
mimeopen -d *.txt
```

should show from list what default editor you can choose to open *.txt

---

### Post by lou6 on 2018-12-12
Well, I removed gedit with synaptic (and Text Editor disappeared from whisker menu) but I still cannot specify mousepad as the default app for text files.  If I right-click on a text file click properties/open with and click on mousepad, "select" is grayed out.

In terminal entering 'mousepad' followed by the name of a text file gives 5 gtk warning messages, the clock spins and the file does not open.

However, the link on my desktop STILL opens the text file it's pointing to (using mousepad)!  Bizarre...

Starting to look like a mimeapps file has been corrupted but I have no idea how - all I did was apply an upgrade sent by software updater.

I have not tried the mimeopen -d *.txt yet - the computer I'm writing from is not the one that is having the problem.  As soon as that machine becomes available I'll try it.

---

### Post by lou6 on 2018-12-12
Just to complicate matters further, when I clicked Software Updater last night I received a message that said I could not run Software Updater until a pending upgrade was done and asked if I wanted to do the upgrade.  I clicked 'yes', 12 packsges downloaded and installed normally and I got a message that my system was up to date.

Then, the problems began.

---

### Post by lou6 on 2018-12-12
Tried mimeopen -d *.txt, got a list of apps, selected '2' (mousepad), selection confirmed.

Still the same results as before - double-click filename, clock spins, file does not open.

Let's give this up guys (unless someone positively knows what's wrong).  I have a tolerable workaround and I can live with it the way it is.

Thanks to you all for your suggestions.

UPDATE:

One final oddity:  If I open mousepad I can choose 'open' and open a text file from there but cannot make double-clicking the file work,

---

### Post by HermanAB on 2018-12-13
The double click launch is defined by the MIME extensions setup as described above.

---

### Post by lou6 on 2018-12-14
The solution to this is here:

[Bug #1778069 “[xfce] nautilus don't open files if set as default...” : Bugs : nautilus package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1778069")

I actually fixed this on my other computer 6 months ago - I have no idea why it just cropped up on the other machine this week.  Something to do with update scheduling I guess.

Anyway, it manifested itself a bit differently this time and I did not recognize it as the same problem.

---

