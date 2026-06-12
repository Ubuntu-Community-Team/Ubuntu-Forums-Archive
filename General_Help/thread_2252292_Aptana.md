---
title: "Aptana"
date: 2014-11-10
forum: General Help
---

### Post by glennbates on 2014-11-10
How do I install Aptana on Ubuntu?

---

### Post by claracc on 2014-11-11
Here, [http://www.sysads.co.uk/2014/06/install-aptana-studio-3-ubuntu-14-04/](http://www.sysads.co.uk/2014/06/install-aptana-studio-3-ubuntu-14-04/) you have a step by step guide.

---

### Post by glennbates on 2014-11-11
I get " cannot find or open Aptana_Studio_3_Setup_Linux_x86_64_3.4.2.zip"

---

### Post by glennbates on 2014-11-11
Ok, scratch the above. I got past that. Now on the command "sudo mv/Aptana_Studio_3 /opt" I get "command not found"

---

### Post by ian-weisser on 2014-11-11
'mv' is the command. There should be a space after it.

---

### Post by glennbates on 2014-11-16
Now I get "mv: cannot stat ‘/Aptana_Studio_3’: No such file or directory"

---

### Post by claracc on 2014-11-17
Could you see in xterm if there is the directory Aptana_Studio_3 after untar the .zip file?

---

### Post by monkeybrain20122 on 2014-11-17
Why make it so complicated? It doesn't need to be install. Just extract it in your home, that's it. Ciick the file AbtanaStudio3.sh to start (if you have click to start or ask what to to do enabled in Nautilus > Exit > Preference > Behaviour > Executable text files), or use the terminal, or make a .desktop file.

You don't need to move it to /opt if you are the only user.

---

### Post by glennbates on 2014-11-24
> **monkeybrain20122 said:**
> Why make it so complicated? It doesn't need to be install. Just extract it in your home, that's it. Ciick the file AbtanaStudio3.sh to start (if you have click to start or ask what to to do enabled in Nautilus > Exit > Preference > Behaviour > Executable text files), or use the terminal, or make a .desktop file.

You don't need to move it to /opt if you are the only user.

Where do I find the file AbtanaStudio3.sh?

---

### Post by monkeybrain20122 on 2014-11-25
In the .zip file. Put it where you want it to be,  right click > extract here.

---

