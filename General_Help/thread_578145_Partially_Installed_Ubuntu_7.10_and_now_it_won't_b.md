---
title: "Partially Installed Ubuntu 7.10 and now it won't boot"
date: 2007-10-16
forum: General Help
---

### Post by chilker on 2007-10-16
This is going to make me sound like a total n00b, I know.

I tried to upgrade to the RC Gutsy Gibbon using the official method of upgrading

update manager -d

so I did that, but I had to leave it--so my computer had been on for a really really long time. I went to school, and slept and stuff, and wasn't using it. But, then, while it was installing, it gave me a strange screen. It was just that ubuntu orange-brown and it looked like the image on my monitor had been moved.

It inexplicably failed during the install of Gutsy. I shrunk that partition and am now using a fresh install of Feisty on a new partition. I have some data, settings, drivers, utilities, bookmarks, saved game files, and various other stuff on that other install of Feisty Gibbon, I guess. It's an incomplete upgrade. I tried using all the previous kernels on that partition, but nothing will work. It says that it can't mount my HDD, and then gives me the aforementioned orange-brown screen.

Any help would be much appreciated. Either just a way to transfer all my settings and stuff to this fresh install, or a way to doctor up the other broken install. Please give me suggestions or clues or just tell me it's all over and I have to get all that stuff again.

Thank you for your time

-chilker

---

### Post by scrooge_74 on 2007-10-16
Did you have /home in a different partition?

---

### Post by chilker on 2007-10-16
Thank you for the quick reply!

/home...

I think I now have two homes...

Since I have two installs of Ubuntu on this harddrive. I fear that if I transferred /home to the new install, then it would bring with it all the stuff that is now *wrong*... and I don't want to screw up another install. 

I should've backed everything up before updating--but, this computer has mainly just been to learn from (I'm just a high school student who likes to mess with computer) but since I've learned a lot, I've found lots of programs and customized things just to how I like them on the other one, and I don't think i really remember how I did everything. So I like the way the other one is and I just want to know if it's possibly to move those settings over here, or selvage that other install.

Any ideas?

Thanks in advance.
-Chilker

---

### Post by scrooge_74 on 2007-10-17
To give you an idea of what I did when I was learning also.

You can have a /home partition separate from the rest of the system and then you can install as many versions of Linux and just tell each version where your /home is.  If there is something wrong with the config of the system it does not apply to the /home. Maybe a few files for your Desktop options (but you can always delete those and start fresh)

I have carried my /home from computer to computer, I have used Ubuntu 6.06 and 6.10 on the same PC for experiments, with different setups for GUI.

Remember the config files for the system are on /etc which are slightly different for each OS you instal (which should be in its own partition), and your /home is just your user files

---

### Post by chilker on 2007-10-17
Ok, so, if I were to copy the files out of /etc concerning my commonly-used programs, then it would bring all my settings to those (if I had them already installed on my new partition).

For instance--if I were to copy and replace the files in /etc concerning gaim, it would add my accounts and passwords (although that's not a hard one to re-do) and if I copied all the files from Firefox, it would bring my cookies, passwords, usernames, add-ons, bookmarks, etc? Or would those specific things be in /home?

thank you for your time.

---

