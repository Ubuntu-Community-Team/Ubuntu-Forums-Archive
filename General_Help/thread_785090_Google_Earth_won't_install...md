---
title: "Google Earth won't install.."
date: 2008-05-07
forum: General Help
---

### Post by Rodhill on 2008-05-07
I have downloaded Google Earth (Linux) and it won't install/open. I get a message saying there is no application to open this .bin file. I am new to Linux can someone help?

Rod

---

### Post by kesman on 2008-05-07
So how did you install google-earth? It is available via synaptic or add/remove applications and works perfectly.

---

### Post by hyper_ch on 2008-05-07
> **kesman said:**
> It is available via synaptic or add/remove applications
After you add the medibuntu repos ;)

---

### Post by kesman on 2008-05-07
Yeah didn't remember that. To do this, open system -> administration -> software sources and add a 3rd party repository:
```
APT line: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
```
and then according to ubuntuguide.org:
> 
    * Download any needed gpg keys and add them to the keylist. This key verifies the repository to your system. The Medibuntu repository (not affiliated with Ubuntu) example is shown: 

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```


This one you should paste into terminal.

---

### Post by vanadium on 2008-05-07
You might also install using the binary from google. However, to run the installer, you first must make it executable. You can do that from the "properties" tab of the .bin file. Once it is made executabe, you run it with

./<name_of_the_file>

(substitute the actual name of the .bin file here)

---

### Post by dcstar on 2008-05-07
> **Rodhill said:**
> I have downloaded Google Earth (Linux) and it won't install/open. I get a message saying there is no application to open this .bin file. I am new to Linux can someone help?

Rod

[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

### Post by Rodhill on 2008-05-07
Thank you all for your help. I will try the suggestions when I get home from work:)

Rod

---

### Post by Rodhill on 2008-05-07
> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

I've tried this and am a little confused what to do. I copied and pasted the first command line which put the URL into Gedit and I saved that as asked. I then  copied and pasted the next command and nothing happened:confused: Am I supposed to do something with the URL in the terminal or what?

Thanks 

Rod

---

### Post by TunaCanTommy on 2008-05-07
There's a nice little tutorial on YouTube that demonstrates how to install a .bin file in Ubuntu.

---

### Post by hyper_ch on 2008-05-07
why not installing from the repos?

---

### Post by NightwishFan on 2008-05-07
Add medibuntu then:
```
sudo apt-get install googleearth-4.3
```

---

### Post by hyper_ch on 2008-05-08
just use googleearth instead of a version number ;)

---

### Post by kesman on 2008-05-08
I think it will install 4.2 if you don't specify the version number, and 4.3 is much more cool :P

---

### Post by hyper_ch on 2008-05-08
you're rigth :)

---

### Post by kesman on 2008-05-08
Of course I am

---

### Post by TunaCanTommy on 2008-05-08
Here's some info from a Google Earth discussion forum:

[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5#)

"Google Earth 4.3 only works in Linux on machines with processors
that support SSE2. This means a P4, A64, or greater is now required."

So, if your system can't support 4.3 you need to stay with 4.2.

---

