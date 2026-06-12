---
title: "Prevent flashplugin-installer from installing?"
date: 2015-04-21
forum: General Help
---

### Post by tensizes on 2015-04-21
I _do not_ want flashplugin-installer to install in my Ubuntu 14.01LTS.  I have tried to prevent it, but something keeps putting it in!

I have non-free stuff enabled, but I want to block flashplugin-installer.  Somehow it keeps inserting itself into firefox or firefox keeps adding it.  I don't want it.  I didn't install it, and I certainly don't want the security vulnerability that comes with it.

Here is what I have tried so far:

I added the following to /etc/apt/preferences:

> Package: flashplugin-installer
Pin: origin ""
Pin-Priority: -1

Package: flashplugin-installer:i386
Pin: origin ""
Pin-Priority: -1

Despite the above in my /etc/apt/prefences I recently found that flashplugin-installer was (again) on my computer, because in a forum I was visiting I noticed that flash material was playing.  I typed "dpkg -l flash" and found that flashplugin-installer had somehow been put in!  So I typed "sudo apt-get remove flashplugin-installer" and that uninstalled flashplugin-installer.  Then I tried installing, to see if I might have put it in myself, but that didn't work.  I got the desired "flashplugin-installer has no installation candidate"...so why and how did it get installed?  How do I stop this piece of very insecure software from installing?

---

### Post by Frogs Hair on 2015-04-21
Hello and Welcome:
 
The package doesn't install by default , but will be installed along with the Ubuntu-restricted-extras package. If using this package you can remove it post installation with the command you already used. 
 ```
sudo apt-get remove flashplugin-installer 
```

---

### Post by tensizes on 2015-04-21
Thanks, but I did do that already; and I set apt so that I could not have installed it myself.  Therefore something is putting it in while I'm not looking.  Do you know what could do that?

---

### Post by deadflowr on 2015-04-21
Do you adobe-flashplugin installed?

---

### Post by tensizes on 2015-04-21
> **deadflowr said:**
> Do you adobe-flashplugin installed?
No, I do not have adobe-flashplugin installed.  I also have uninstalled the flashplugin-installer package.  Currently there is no flash on the computer.  I just think that it will install itself again somehow.

---

### Post by ken0069 on 2015-04-21
Might I suggest that you install "Flashblock" in Firefox add on extensions.  That will prevent flash from running automatically if it gets installed again without your knowledge.  I use that on my systems and it works well.

---

### Post by tensizes on 2015-04-21
Perhaps Firefox installs it?  What I might do is just install it and then take away all of its execution permissions and pin it, so that it can't update or run.

---

### Post by deadflowr on 2015-04-21
> **ken0069 said:**
> Might I suggest that you install "Flashblock" in Firefox add on extensions.  That will prevent flash from running automatically if it gets installed again without your knowledge.  I use that on my systems and it works well.

You don't even need that anymore.
Current fiirefox version have builtin function to disable flash.
Open Tools >> Addons goto Plugins, toggle shockwave flash to either "ask to activate" or "never activate".
Close.
Now flash won't run unless you tell it to.
And should only run on sites you have told it to.

---

### Post by tensizes on 2015-04-21
> **ken0069 said:**
> Might I suggest that you install "Flashblock" in Firefox add on extensions.  That will prevent flash from running automatically if it gets installed again without your knowledge.  I use that on my systems and it works well.
Good idea, although I already use the noscript extension.  Sometimes I will visit youtube which offers some of its videos in h.264 instead of Flash.  My suspicion is that firefox somehow managed to install flash, but I do not know.  I want h.264 video, just not Flash since it is insecure.

---

### Post by tensizes on 2015-04-21
Thanks everyone for all the suggestions.  I guess this is just something I'll have to work around somehow.

---

### Post by monkeybrain20122 on 2015-04-21
> **ken0069 said:**
> Might I suggest that you install "Flashblock" in Firefox add on extensions.  That will prevent flash from running automatically if it gets installed again without your knowledge.  I use that on my systems and it works well.

Well there has been no need for Flashblock for quite a while. Now the function is built into Firefox, just go to Tools > Addons > Plugins and set the preference to "ask to activate" and that is the same as Flashblock. But that doesn't answer OP's question.

@OP No, Firefox does not install flash by itself. in fact nothing can install without you giving your password. I am sure you did it somehow. If you use synaptic to update you can check your update history.

---

### Post by deadflowr on 2015-04-21
> **monkeybrain20122 said:**
> Well there has been no need for Flashblock for quite a while. Now the function is built into Firefox, just go to Tools > Addons > Plugins and set the preference to "ask to activate" and that is the same as Flashblock. But that doesn't answer OP's question.

@OP No, Firefox does not install flash by itself. in fact nothing can install without you giving your password. I am sure you did it somehow. If you use synaptic to update you can check your update history.

You can also look for the ubuntu-restricted-extras package. As the flashplugin-installer could/would be installed through that as well.

---

### Post by Dennis N on 2015-04-21
Probably too late now, but could you be confusing flashplugin-installer with the actual flash plugin? Removing the first may not remove any plugin that's already been installed. My assumption would be that it doesn't, but I've never tested the idea.

I would think you need to delete the plugin itself, which is **libflashplayer.so**

Or, you could just rename it and get the same effect as deleting. That would also give you the option to restore it.

---

### Post by Vladlenin5000 on 2015-04-21
> **Dennis N said:**
> Removing the first may not remove any plugin that's already been installed. My assumption would be that it doesn't, but I've never tested the idea.

Your assumption is correct.

---

### Post by tensizes on 2015-04-22
> **Dennis N said:**
> Probably too late now, but could you be confusing flashplugin-installer with the actual flash plugin? Removing the first may not remove any plugin that's already been installed. My assumption would be that it doesn't, but I've never tested the idea.

I would think you need to delete the plugin itself, which is **libflashplayer.so**

Or, you could just rename it and get the same effect as deleting. That would also give you the option to restore it.
Good ideas. 

Looking at the modules: taking a look in /lib/x86...  and /usr/lib/x86... I do not see any libflashplayer.so files.  I think that is where they would be, so maybe the uninstall process removed it.

I will see if I can get it to auto install again, click on some youtubes, run update etc.  If it doesn't happen I will drop the subject.

---

### Post by deadflowr on 2015-04-22
Youtube videos will run without flash.
They can use HTML5.
So beware of that.

---

### Post by Dennis N on 2015-04-22
> **tensizes said:**
> Looking at the modules: taking a look in /lib/x86...  and /usr/lib/x86... I do not see any libflashplayer.so files.  I think that is where they would be, so maybe the uninstall process removed it...

To find the location of the flash plugin (libflashplayer.so) being used by Firefox, type "about:plugins" in the Firefox address bar. Among the entries, you should find:

```
Shockwave Flash

    File: libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 11.2.202.457
    State: Disabled
    Shockwave Flash 11.2 r202
```

which displays the location of the plugin.

---

