---
title: "get vimtutor on ubuntu"
date: 2007-02-28
forum: General Help
---

### Post by LSparky on 2007-02-28
I need vimtutor for a class im taking.
fedora 6 has it, but i would like it for ubuntu so i dont have to use fedora.
does anyone know how i can get vimtutor on ubuntu.
i checked the ubuntu repositorys and couldnt find it.

---

### Post by Cathead Fred on 2007-03-01
Hi LSparky,

Sorry to hear about your problem. I believe the packages that work on Fedora use .rpm. You want to convert vimtutor from .rpm to .deb. Here are a couple of links that show how to do that with a program called alien.

#1 [http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

#2 [http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)

 Good luck and post your progress

Cathead Fred

---

### Post by watchmancole on 2007-03-01
Hi L SParky,

Do you mean the Vimtutor helper script? If so Ubuntu 6.06 Dapper Drake and above have Vimtutor included in the vim-common package (earlier version may have had it also). So if you install vim you should have it available. 

Hope this helps.

---

### Post by userlaur on 2007-03-14
> **LSparky said:**
> I need vimtutor for a class im taking.
fedora 6 has it, but i would like it for ubuntu so i dont have to use fedora.
does anyone know how i can get vimtutor on ubuntu.
i checked the ubuntu repositorys and couldnt find it.

Hello,
I had the same problem, and while thinking about it in the middle of the night and looking at all those packages that contained "vim" in their name, I decided to install the package called vim-full. => And afterwards I typed vimtutor at the console and it worked.
So, that was it: vimtutor can be found in the vim-full package.

Laur.

---

### Post by loza on 2008-01-05
Hey

Thanks for the post worked a treat!

When I ran vimtutor before installation I got this below:

```
 vimtutor
The program 'vimtutor' is currently not installed.  You can install it by typing:
sudo apt-get install vim-runtime
bash: vimtutor: command not found

```

So I installed the runtime and I still did not get the script. But after finding this post and installing vim-full, it worked!

Might this be a bug in Gutsy???

thanks!

loza

---

