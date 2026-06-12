---
title: "Is this possible? - kde-core"
date: 2006-10-27
forum: General Help
---

### Post by ehird on 2006-10-27
Is "apt-get install kde-core" then "apt-get remove gnome <command to remove all gnome apps and things it depends on etc>" dangerous or will it give me what I intend? (i.e. a lightweight kubuntu basically).

I don't want to use Kubuntu because it is very unstable for me.

---

### Post by kidders on 2006-10-27
Hi there,

Removing Gnome is a big job ... you won't be able to do it with a single "apt-get". Even if you did though, you'd be surprised how many applications depend on Gnome libraries -- are you sure you'd be able to live without them?

Assuming you can, what you want to do *is* possible, but won't you just be re-introducting the stability problems you referred to?

---

### Post by Christmas on 2006-10-27
"apt-get remove gnome" will only remove package "gnome" and not the other GNOME applications. You can remove the whole GNOME by following [these](http://www.psychocats.net/ubuntu/purekde) instructions. I used to install kde-core on Debian and now I did it on Kubuntu. Here's what you do:

1. Get Kubuntu Alternate CD
2. Install only the base system (Install a server)
3. Configure the network and your /etc/apt/sources.list file
4. Type:
```
apt-get update
apt-get install x-window-system-core kdm kde-core
```
This is it. Restart or type "sudo kdm" to get in it. You'll be presented with a non-customized KDE, only a few application, and all is let for you to configure. When only in CLI mode, you can navigate through the virtual consoles by using Ctrl+Alt+F1 (through F6), so while the packages are beeing installed, try Ctrl+Alt+F2 and play a little in CLI. For step 1, consider also the Ubuntu Alternate CD, no matter which one you'll use, you'll get the same result.

The second option would be to make an offline repository that includes x-window-system-core, kdm, kde-core and their dependencies on a single CD, but I can't help you with that since I don't know how to do it. It should be simple anyway. If you decide for this one, just type "sudo apt-cdrom add" to add your CD to the sources.list file.

---

### Post by ehird on 2006-10-27
I think it's Kubuntu thats the problem, not KDE. It's "the demon start screen" - after a few restarts the system will show a logo and a blank progress bar after two flashes of KDE, and stays there hanged.

Edit: I would like to use just KDE stuff, yes. Mixing non-native apps feels odd to me.

---

### Post by kidders on 2006-10-27
Hey again,

> **ehird said:**
> I think it's Kubuntu thats the problem, not KDE. It's "the demon start screen" - after a few restarts the system will show a logo and a blank progress bar after two flashes of KDE, and stays there hanged.

Edit: I would like to use just KDE stuff, yes. Mixing non-native apps feels odd to me.

This sounds suspiciously like an X-related problem, which are often relatively easy to correct.

In any case, KDE & Gnome apps are just as "native" to eachother, really ... they just depend on a different set of libraries. Imo your choice of app should be governed by which does the job better, not which system libraries they happen to use.

That said, if you're low on RAM/disk space, or don't want to give up certain KDE niceties, youy might have a reason to stick purely to KDE.

---

### Post by ehird on 2006-10-27
Yeah, gnome's a bit laggy to me, and some KDE features are really nice IMO. By the way, when I said <command to remove gnome and all progs and libs it uses> i meant I didn't know what to fill in that spot to do it :P. Would I have to do the monstrosity on [http://www.psychocats.net/ubuntu/purekde?](http://www.psychocats.net/ubuntu/purekde?)

Edit: Problem! I've installed extra software. How can I just wipe all the apps i have and gnome? (Note: Not the libraries or anything) (Well, GNOME's libraries)

---

### Post by kidders on 2006-10-27
More or less, yes. The link you posted is maybe a little extreme, but that just means the occasional package may put itself back on again later, to meet a dependency.

I could be wrong, but afaik, KDE is quite a bit more heavyweight than Gnome. If Gnome lags on you, then KDE *should* be worse.

**Edit:** You could try a reverse dependency check, to see what apps depend on the things you're removing, which would (I suppose) give you a list of Gnome applications. I'm not altogether sure how apt-get behaves when it comes to swiping indirect dependencies out from under something.

---

### Post by Christmas on 2006-10-27
[quote=ehird]Would I have to do the monstrosity on [http://www.psychocats.net/ubuntu/purekde?](http://www.psychocats.net/ubuntu/purekde?)[/quote]
I guess yes, that's the only option you have if you don't want to make a clean install as I did and explained in the above post. The thing is, I think, you can't track the exact GNOME libraries and programs you have installed, so that command will  remove all the GNOME-related packages (included by default in Ubuntu I guess, not all in the repos - this is why a recommend a clean install of kde-core), no matter if they are installed or not (it will remove the installed ones).

---

### Post by ehird on 2006-10-27
Maybe it's just the programs I use then (i.e. gaim). I guess I'll TRY amarok on gnome... *twitch*. But it'll install lotsa KDE libs, right? Is there an easy way to vanquish those libs if i uninstall amarok?

---

### Post by Christmas on 2006-10-27
[quote=kidders]I could be wrong, but afaik, KDE is quite a bit more heavyweight than Gnome. If Gnome lags on you, then KDE should be worse.[/quote]
Not quite. I think it depends, for me KDE always works faster (from the applications to interface's speed).

---

### Post by Christmas on 2006-10-27
Yes it is, if you install and uninstall packages using "aptitude".
```
sudo aptitude install package_name
```
```
sudo aptitude remove package_name
```
And it will remove the libraries and dependencies if they are not used anymore by another application.

---

### Post by ehird on 2006-10-27
Oh, and I was considering your clean install thing, Christmas, but here's the catch: alternate install never really worked right for me (5.05 days when it was the only way). The desktop install magically works for me, though... And I'm sure I'm not doing anything wrong.

Edit: I'm sure it's possible using apt-get, if you use synaptic's thing to remove unused dependencies, isn't it?

---

### Post by kidders on 2006-10-27
> **Christmas said:**
> Not quite. I think it depends, for me KDE always works faster (from the applications to interface's speed).

Hmm... interesting. Thanks for the info :-) I'm a big KDE fan, so it's nice to know it's fast too!

---

### Post by ehird on 2006-10-27
eh, so i take it there's no easy way to just <wipe gnome its dependencies and all apps> and then <install kde>.

---

### Post by Christmas on 2006-10-27
[quote=ehird]Oh, and I was considering your clean install thing, Christmas, but here's the catch: alternate install never really worked right for me (5.05 days when it was the only way). The desktop install magically works for me, though... And I'm sure I'm not doing anything wrong.[/quote]
It should work... If not try installing the base system from the Server CD. It installs only the base system, and you can go from there installing x-window-system-core, kdm and kde-core. But since you might not want to reinstall, you can try to remove manually with Synaptic as you say, but it would be a lot of work and you can remove by accident some packages you think you don't need but are needed by another program... I think it's not a good way. You can also try installing Ubuntu from the desktop CD and after the installation install "kdm" and "kde-core" and then remove the GNOME packages following the link I pointed you to. It's up to you what way you choose, but what I'm trying to say is that removing "all" the packages which you think you don't need might be a mistake. An easier way to do what you say I can't find, maybe someone else? I'd definitely go for the server install then fetch only the packages I need. It's cleaner in my opinion.

---

### Post by ehird on 2006-10-27
There maybe is a problem - i dunno if i'd have the patience to get my modem working via the terminal, its hard enough with a GUI. Anyway, aptitude amarok  to test it...

---

