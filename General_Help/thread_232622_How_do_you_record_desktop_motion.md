---
title: "How do you record desktop motion?"
date: 2006-08-09
forum: General Help
---

### Post by boom2k1 on 2006-08-09
How do you record desktop motion?
-i.e. i want to show off the cool feature of a widescreen desktop

Thanks

---

### Post by msak007 on 2006-08-09
In Windows I used to use SnagIt, but I don't believe there's a native Linux app that does video recording of the Desktop. [This]("http://wolphination.com/linux/2006/06/30/how-to-record-videos-of-your-desktop/") is the closest thing I could find to what you're looking to do - the end result is a Flash video. I'll have to try it myself as it looks really interesting. A big plus is that the tutorial author is using Ubuntu Dapper so it should be pretty straightforward.

---

### Post by boom2k1 on 2006-08-09
thanks!!!

---

### Post by den_ on 2006-08-09
Istanbul??? New version can even record sound, but it is not available on repos.

---

### Post by msak007 on 2006-08-09
Wow I've never heard of Istanbul, but I believe this is exactly what the OP was looking for. Thanks for the suggestion, I'll have to give this a try as well.

---

### Post by Tomosaur on 2006-08-09
I use XVidCap. It also records sounds, but not all that great.

---

### Post by msak007 on 2006-08-09
The author of the tutorial I linked to did mention XVidCap as an option, but said that it's a lot harder to set up.

---

### Post by Irony on 2006-08-09
You can download the debian xvidcap from here;

[https://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=430409](https://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=430409)

It installs with the GDebi installer, so you'll find its then listed in Synaptic, works fine on my machine.

---

### Post by den_ on 2006-08-14
I have just compiled xvidcap it works fine, a lot better then istanbul, but it doesn't record sound. any ideas how could I fix it?

I have no oss compiled in kernel. Use alsa emulation and it works just fine with ut2004 for example, although I had to add some lines in /etc/modutils/alsa-base becouse alsa driver didn't have default configuration to support oss emulation for my soundcard (intel high definition audio).

---

### Post by Irony on 2006-08-14
Have you enabled audio in the preferences section?

---

### Post by Irony on 2006-09-03
Just installed the latest xvidcap (xvidcap 1.1.4rc1) from;

[http://sourceforge.net/project/showfiles.php?group_id=81535](http://sourceforge.net/project/showfiles.php?group_id=81535)

Its seems bug free on my Dapper system - its Debian, so is easy to install by double clicking on it.

---

### Post by PriceChild on 2006-10-29
I've got some debs here i built for recordmydesktop.

Using Beryl/AIGLX, i can't capture beryl effects :(

They're Edgy packages.

---

### Post by iovar on 2006-10-30
@PriceChild:

Using properly accelarated AIGLX/compiz-beryl won't work unless you enter
the switces --full-shots --with-shared, but then it becomes a resource
hog. 
If you have automake installed you can try the CVS version under the
module rMD-exp. It still needs those switches and it doesn't play nice
with the interface but it can do a lot better, since it does the encoding
after it finishes.

Meanwhile I'm working on finding a better solution to this... ](*,) ](*,) ](*,)

---

### Post by jordilin on 2006-10-30
You can use byzanz, the desktop recorder. It records what's going on in your pc and produces a .gif file, so it can be reproduced in any browser. It's in the repos.

---

