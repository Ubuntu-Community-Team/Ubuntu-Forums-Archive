---
title: "How to copy a file?"
date: 2020-11-05
forum: General Help
---

### Post by rbscebu on 2020-11-05
I cannot get my Lubuntu 20.04 to boot (again). This happened before, about a month ago. I spent 4 days trying to fix the problem and then gave up. I just reinstalled a new copy of Lubuntu 20.04. With this same problem now occurring again, I wish to reinstall Lubuntu 20.04.

I can boot to my Lubuntu 20.04 installation DVD. Before I reinstall,  I want to copy a Veracrypt "container" to a USB stick so as not to loose the contents. I can access the internal SSD on my PC using the Lubuntu installation DVD and navigate to where the "container" is. When I right-click on the "container", the copy option is greyed out. Properties>Permissions in Ownership shows Owner: 1000 (greyed out) and Group: 1001 (greyed out). Access Control shows Owner: Read and write, Group: Forbidden and Other: Forbidden.

How can I copy this "container" to m USB stick?

---

### Post by HermanAB on 2020-11-05
Well, note that madness is doing the same thing over and over, expecting a different result...

Linux is very good, but it is not tested on every machine in the world.  Some devices have problems with some distros.

If the machine screwed up 3 times with the same distribution, then it may be time to try a different distribution, such as Fedora or Arch.

---

### Post by rbscebu on 2020-11-05
I agree but only twice so far and will be doing so when I have the data available to download a new distro. Until then I am stuck with Lubuntu 20.04 and its recurring problem on my PC. Until then, back to my question.

---

### Post by ActionParsnip on 2020-11-05
If you run pcmanfm2 using sudo it should give access, or copy it in the terminal.

---

### Post by HermanAB on 2020-11-05
In general:
$ sudo cp /where/from /where/to

or as suggested above:
$ sudo pcmanfm2

Then, watch the error messages in the terminal.

Maybe this explains it:
[https://www.bbc.com/news/science-environment-54817124](https://www.bbc.com/news/science-environment-54817124)
;)

---

