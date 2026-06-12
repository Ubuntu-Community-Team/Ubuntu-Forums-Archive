---
title: "Real Player question"
date: 2008-06-16
forum: General Help
---

### Post by jras20 on 2008-06-16
Can I install any Real player?  I'd like either 10 or 11.  I see Real 11 is Vista and XP only, but can I get a earlier version for streaming audio?
Thanks

---

### Post by jras20 on 2008-06-16
Well I went back looks like they have it for Ubuntu now.  Now how do I install .bin files?   I still have not got that down yet.
What is the command?

---

### Post by MacAnthony on 2008-06-16
Wow, do they have an unbelievable lack of info on their site. My guess is that it's a binary executable file. Try typing in a terminal:
./<filename>.bin

---

### Post by drs305 on 2008-06-16
Some other media players will play Real Player files, but if you still want to install RealPlayer 11, here is how:

In terminal, move into the same folder as the bin file. Then:
```

chmod a+x RealPlayer11GOLD.bin

```

This will turn the file's icon into a blue diamond.

Then in terminal to start the installation:
```

./RealPlayer11GOLD.bin

```


Note: If you do install it, keep any folders, especially the "postinst" folder, that are created during the installation. The reason is that bin files install programs outside synaptic and apt-get/aptitude and cannot be uninstalled via those means. Inside the Realplayer folder are the uninstall scripts that won't be available should you delete that folder after installation.

---

### Post by jras20 on 2008-06-16
I still cant get it to install...

---

### Post by Pjotr123 on 2008-06-16
Try this for 100 % multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

And afterwards step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by drs305 on 2008-06-16
> **jras20 said:**
> I still cant get it to install...

You are going to make me install Real Player 11 again, aren't you! ;-)  It's okay, I've done it half a dozen times for others (before I uninstalled it again).

I downloaded the file and it is on my Desktop: RealPlayer11GOLD.bin The icon on my computer looks like a text file.
Note that correct case is required: realplayer does not equal RealPlayer

Change to the directory in which the .bin file is located. For simplicity, if it is not on your Desktop, move it there now. After moving it, run the following two commands:

```
cd ~/Desktop
ls
```
You should see RealPlayer11GOLD.bin listed.

Make it executable. Hint: If you type instead of cut & paste, after typing the first few letters of RealPlayer11GOLD.bin you can hit the tab key and it will autocomplete it:
```
chmod a+x RealPlayer11GOLD.bin
```
If you look at the file icon, it should have changed into a blue diamond.

Make an installation directory and change ownership to yourself. You can select any location you desire. If you choose a system folder (such as opt) you will have to change the ownership of the new folder to yourself. Make sure you substitute your own username:
```
sudo mkdir /opt/realplayer
sudo chown -R yourusername:yourusername /opt/realplayer

```

Start the installation. The same tab trick works here if you are typing:
```
./RealPlayer11GOLD.bin
```

Press Enter. It will run for a bit and then ask where you want to install the program: (/opt/realplayer)

Let the install files do their thing. At several points it may appear to hang. Give it a few minutes and the hit enter if it hasn't continued on its own.

It will say finished and then cleaning up installation files.
Important: In the /opt/realplayer folder there is a "postinst" folder. This has the necessary scripts to uninstall the program. Do not remove these files.

You can delete anything remaining on your Desktop relating to RealPlayer. RealPlayer11 will now be listed under the Sound & Video menu.

---

### Post by ikki_72 on 2008-06-17
how do i uninstall this shiz btw?

---

### Post by jras20 on 2008-06-17
I'll try that thanks, I just want some streams not so much the program but just the streams.

---

### Post by fromgi on 2008-06-22
You mention that VLC will play RealPlayer files, but I can't get it to play RAM videos.  Is there something in the prefrences or elsewhere I need to do?

---

### Post by drs305 on 2008-06-22
> **fromgi said:**
> You mention that VLC will play RealPlayer files, but I can't get it to play RAM videos.  Is there something in the prefrences or elsewhere I need to do?

Actually, I don't think you can use VLC. I've gone back and edited my original post to reflect this.

---

### Post by fromgi on 2008-06-22
> **drs305 said:**
> Actually, I don't think you can use VLC. I've gone back and edited my original post to reflect this.

Thank you for the clarification.

Can you please tell me what, if anything you needed to do in order to get files the a RAM extension to play?  I can get all these to play except the RAM's.  [This is the link.]("http://www.linspire.com/products_linspire_whatis.php?tab=compatibility")

Thank you!

---

