---
title: "Having Vista and Ubuntu Access One HDD?"
date: 2008-03-02
forum: General Help
---

### Post by M4v3r1kk on 2008-03-02
So I'm pretty new with Ubuntu. I've recently installed it and haven't had much time to mess around but I'm already thinking about an organized way of running things.

My idea is to have Vista on the C drive as it already is and put Ubuntu on the D drive. This means both of my 80GB drives in my laptop will be running either Ubuntu or Vista.

My question is: can I have both of them access an external HDD? So can I have Office 2007 and have Vista and Ubuntu access it, save files and open files made in either OS?

Any guides or FAQs on the web that are **thorough** are welcome.

note: please explain things to me. I'm not some Ubuntu genious ;) .

---

### Post by SpaceTeddy on 2008-03-02
a default ubuntu installation (7.10) should be able to read/write ntfs and fat by default, thus all you need in ubuntu is to plug the drive in and it would work. 
Also, ubuntu (if you installed it after you installed vista) will automaticially create a shortcut on your desktop for your vista drive which you can access normally, thus writing to the vista drive directly (C: in your case)

The only thing you have to make sure is that the drive you want to use is NOT formated with a linux FS, since windows cannot read those. But afaik linux can read/write any windows FS that is thrown at it.

i hope i interpreted your question right...

---

