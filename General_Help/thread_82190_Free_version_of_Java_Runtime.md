---
title: "Free version of Java Runtime ??"
date: 2005-10-26
forum: General Help
---

### Post by kudu on 2005-10-26
There was a free version of the Java Runtime Environment in  the repositories but I can't find it now. I just reinstalled Breezy and for some reason it has disappeared. Anyone know what it's called and where I can find it ?

kudu

---

### Post by frenkel on 2005-10-26
The java runtime is called j2re1.4
Install it like this:
$ apt-get install j2re1.4

Good luck

---

### Post by vassalle on 2005-10-26
whats the difference with the non-free ones ?

---

### Post by kudu on 2005-10-26
Tried it, but package is unavailable.

There was one made by somebody other than Sun kinda like Mesa and OpenGL. I think it started with a B. But I can't remember. Argh! I could manually install no sweat but I'd rather just use that free one since all I want it for is running VASSAL.

---

### Post by kudu on 2005-10-26
[QUOTE=vassalle]whats the difference with the non-free ones ?[/QUOTE]

Not sure other than you don't need to sign any user agreements with Sun.

---

### Post by frenkel on 2005-10-26
[QUOTE=kudu]Tried it, but package is unavailable.

There was one made by somebody other than Sun kinda like Mesa and OpenGL. I think it started with a B. But I can't remember. Argh! I could manually install no sweat but I'd rather just use that free one since all I want it for is running VASSAL.[/QUOTE]
Works here, it was made by Blackdown.
Do you have multiverse in your sources.list?

---

### Post by kudu on 2005-10-26
Got it! Had to change my sources.list to a newer "official" version posted in another thread.

Thanks!

---

### Post by DogTags on 2005-10-26
What's the other thread?

Better yet, what are the changes you needed to make?

Thanks :)

---

### Post by TimonVO on 2005-10-26
Actually, I think Sun's JRE is the best one and most spread. I don't see any reason why you should use a commercial one.

---

### Post by frenkel on 2005-10-26
[QUOTE=TimonVO]Actually, I think Sun's JRE is the best one and most spread. I don't see any reason why you should use a commercial one.[/QUOTE]
Read the thread, this is not a commercial one, it's a free one, with a more "friendly" license (IE. it can be included in Ubuntu's repository's). And everything works just the same, every applet created for Sun's JRE works in Blackdown's JRE also.

---

### Post by Hallavej on 2005-10-26
[QUOTE=frenkel]Read the thread, this is not a commercial one, it's a free one, with a more "friendly" license (IE. it can be included in Ubuntu's repository's). And everything works just the same, every applet created for Sun's JRE works in Blackdown's JRE also.[/QUOTE]

No not true. Blackdown is in version 1.4 and Sun is 1.5. And that makes a difference.     Eg. your browser plugin will not work on many site because version 1.5 is nessesary.

---

### Post by frenkel on 2005-10-26
[QUOTE=Hallavej]No not true. Blackdown is in version 1.4 and Sun is 1.5. And that makes a difference.     Eg. your browser plugin will not work on many site because version 1.5 is nessesary.[/QUOTE]
1.5 is still in development at Blackdown, but I haven't found any applet which doesn't work. I know there are difference between 1.4 and 1.5, but as long as the developer didn't us any 1.5 specific functions used, it will work. And to be honest, I haven't found any 1.5 specific applets yet. As you could read in the starting post, the topic started wanted to install it for one specific app/applet, so Blackdown just works.

And btw, most other distro's (Gentoo aswell) still use the 1.4 version of Java, as the 1.5 version isn't tested enough according to them.

Frank

---

