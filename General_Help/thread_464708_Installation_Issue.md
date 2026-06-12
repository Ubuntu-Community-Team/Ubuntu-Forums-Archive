---
title: "Installation Issue"
date: 2007-06-05
forum: General Help
---

### Post by MrBungle821 on 2007-06-05
Well, I used the file provided in[ this site]("http://www.gnutellaforums.com/general-linux-support/39850-how-install-limewire-ubuntu-debian.html").

And about halfway through the installation of java, I closed everything. As I thought it was installing wayyy to slowly, and thought it froze on me :(. Yeah, bad call. And after a restart of everything, I still get this message.

[IMG]http://i7.photobucket.com/albums/y283/mrbungle821/Error.png[/IMG]

Any help?

---

### Post by thelocust on 2007-06-05
Did you run sudo dpkg -- configure -a in terminal.  If not run it and post the resaults.

---

### Post by MrBungle821 on 2007-06-05
Well, that too isn't even working. I got to the password time just once, and now it just isn't working, not even getting to that. UGH. I really like Ubuntu and everything but if stuff like this is going to keep happening, I just may have to go back to XP :(

---

### Post by thelocust on 2007-06-05
so when you enter the command it asks for your root password and then nothing happens?

---

### Post by MrBungle821 on 2007-06-05
No, nothing happens, or this happens.

Before-[IMG]http://i7.photobucket.com/albums/y283/mrbungle821/Before.png[/IMG]

After- [IMG]http://i7.photobucket.com/albums/y283/mrbungle821/after.png[/IMG]

---

### Post by thelocust on 2007-06-05
sorry theres a space in between dpkg and --. Its sudo dpkg --configure -a

---

### Post by MrBungle821 on 2007-06-05
Well, that did get me somewhere!!! haha, now what? (Sorry, im clueless)

[IMG]http://i7.photobucket.com/albums/y283/mrbungle821/Ohlord.png[/IMG]

---

### Post by thelocust on 2007-06-05
sorry man **sudo** space **dpkg** space **--configure** space [B]-a
[/B]
It gets easier I promise. I usually just copy and paste commands I get off the forums lowers the chance of me screwing up I do fine on that by my self.

---

### Post by thelocust on 2007-06-05
By the way [here's]("http://linuxcommand.org/") a good tutorial for terminal commands. It sucks at first but now there's allot of operations that I prefer to use terminal for. Good luck. Let me know if that fixed your problem.

---

### Post by MrBungle821 on 2007-06-05
Well, I did that, just copied and pasted what you said. And it just doesnt work. It brings up the same options. UGH. This was the last program I needed too. If I can't get this to work. It's XP all over again :(

---

### Post by jfinkels on 2007-06-05
Do the following commands:
```
sudo dpkg --configure -a
sudo apt-get -f install

```

If you want to install java, type the following:
```
sudo aptitude install sun-java6-jre
```

---

### Post by MrBungle821 on 2007-06-05
THANK YOU!!! :)

yall just kept a Ubuntu user. Feel happy. Everythings worked. I got iTunesish (Rythembox to finally play MP3's, and now this. yay!)

---

### Post by MrBungle821 on 2007-06-05
Well, I take back what I was saying. I had both Limewire and Frostwire installed. Both with my Java stuff. But I click on either, and nothing comes up. UGH. Now what? :(

---

### Post by jfinkels on 2007-06-05
> **MrBungle821 said:**
> Well, I take back what I was saying. I had both Limewire and Frostwire installed. Both with my Java stuff. But I click on either, and nothing comes up. UGH. Now what? :(

Oy don't need to use Limewire if you have Frostwire :P

Reinstall frostwire like this:```
sudo aptitude reinstall frostwire
```

Open frostwire from the terminal to view the error message:
```
frostwire
```

---

### Post by MrBungle821 on 2007-06-05
Well, I just updated my Java too! UGH. But this is what it said. First part is the reinstallation, and it didnt work...then this..UGH

[IMG]http://i7.photobucket.com/albums/y283/mrbungle821/UGh.png[/IMG]

---

### Post by jfinkels on 2007-06-05
> **MrBungle821 said:**
> Well, I just updated my Java too! UGH. But this is what it said. First part is the reinstallation, and it didnt work...then this..UGH

What is the output from this command?```
sudo update-alternatives --config java

```

You can just select and copy and paste, no need to take a screenshot.

---

### Post by MrBungle821 on 2007-06-05
YAY! It worked! WOOHO. thanks man. But which is better? Frostwire, or Limewire? UGH. Because I read a review, and it said limewire was better. I used Frostwire on XP though, for security reasons, but thats not an issue anymore. So yeah, which to use? And which to uninstall. Speaking of which. How do I uninstall the program I dont want?

---

### Post by jfinkels on 2007-06-05
> **MrBungle821 said:**
> YAY! It worked! WOOHO. thanks man. But which is better? Frostwire, or Limewire? UGH. Because I read a review, and it said limewire was better. I used Frostwire on XP though, for security reasons, but thats not an issue anymore. So yeah, which to use? And which to uninstall. Speaking of which. How do I uninstall the program I dont want?

You want to use frostwire because it's open source software and it won't bug you about upgrading to pro version. 

Here's a website with info on installing: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

In general, use the package manager (or 'aptitude' as I suggest in my above posts) exclusively, except in rare cases. To uninstall, type the following:```
sudo aptitude remove frostwire
```or whatever the name of the package you want to remove is.

---

### Post by MrBungle821 on 2007-06-05
Awsome. i'm really liking Sudo and Terminal. But yeah, it's not removing Limewire. I decided to keep Frostwire, though it doesn't hold a very good connection. But thats fine. (How do I speed that up?) And yeah. I did 

sudo aptitude remove LimeWire

---

