---
title: "java install"
date: 2005-07-28
forum: General Help
---

### Post by storybookhero on 2005-07-28
I'm having difficulty installing java I think they changed the name in the repository...does anyone know what they change it to or an alternate sire to get java from for easy installl....?

_Ubuntu n0000000b constantly posting and getting awesome results!!!

Jeff

---

### Post by kevcart3 on 2005-07-28
The package name is (don't know what you were trying) "sun-j2re1.5".

On a second note, ensure your /etc/apt/sources.list matches the one [here](http://ubuntuguide.org/#extrarepositories) . If not, follow the instructions, including "apt-get update"

then try to "apt-get install sun-j2re1.5"

---

### Post by storybookhero on 2005-07-28
that didnt help either. It said something like I needed to do an apt get update so I did that and it brought be back to the same thing...this is frustrating...does anyone have the deb file or know how to get it?

---

### Post by kevcart3 on 2005-07-28
[QUOTE=storybookhero]that didnt help either. It said something like I needed to do an apt get update so I did that and it brought be back to the same thing...this is frustrating...does anyone have the deb file or know how to get it?[/QUOTE]

Could you give a little more info on what the error is, but just by looking at what info you gave, iy looks like apt cannot connect to the servers that have the package.

I had a problem similar to this, although it wasn't for java.

Try this:

in your sources.list file that is the same from ubuntuguide, you will see most servers have a "http://us." in front of them, try removing the "US." from all the servers.

For Example:

"deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe"

instead of:

"deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe"

then try "apt-get update"

then try "apt-get install j2re1.5"

If not, please post some more info on the error you are getting.

---

### Post by xmastree on 2005-08-06
Can I jump in here?

```
root@ubuntu:/home/chris # apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
root@ubuntu:/home/chris # apt-get install j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package j2re1.5
root@ubuntu:/home/chris #

```That's what I get when I try.

If I look [here](http://archive.ubuntu.com/ubuntu/pool/universe/s/) I don't see it there either.

 :-?

---

### Post by Rule on 2005-08-06
I followed the guide at [http://www.ubuntuguide.org/4.10/index.html](http://www.ubuntuguide.org/4.10/index.html) (I know it's for warty) but it works in hoary and installed with no problems at all.

---

### Post by xmastree on 2005-08-06
Great! thanks. Got it now. Although I almost didn't...

It's jre-1_5_0_04 now, not _01 and I forgot to change it in one of the commands... :roll: 

Still, all's well that ends well. Thanks Rule!

---

