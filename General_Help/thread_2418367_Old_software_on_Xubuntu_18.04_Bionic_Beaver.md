---
title: "Old software on Xubuntu 18.04 Bionic Beaver"
date: 2019-05-06
forum: General Help
---

### Post by radu19842 on 2019-05-06
Good morning and a great new week start , i have a question...or two : I need an older version of Blender like the ones in the next link [https://download.blender.org/release/](https://download.blender.org/release/) but i dont know if it's possible and if it is possible how can do it in Xubuntu 18.04 Bionic Beaver , and not just blender (though i really need older version) but other old software versions too ? !
Thank you and have a great day !

---

### Post by Claus7 on 2019-05-06
Hello,

unfortunately there is no easy way as far as I know. You could download the deb file from here:
[https://packages.ubuntu.com/search?keywords=blender&searchon=names&suite=disco&section=all](https://packages.ubuntu.com/search?keywords=blender&searchon=names&suite=disco&section=all)

depending on the version you wish to install and then issue the command:
sudo dpkg -i <name>.deb

and provide your password. 

Other than that you could install it manually from the links you provide, yet you will have to take care of all the dependencies on your own, something that might not work, since many packages needed for the installation might be old ones that conflict with the ones already installed.

If the first way works then most probably you are ok, yet if not, then things are getting harder. The same applies to other old software versions as well.

Regards!

---

### Post by HermanAB on 2019-05-06
Install an old version of Ubuntu/Debian in a VM?

---

### Post by &amp;KyT$0P# on 2019-05-06
> **radu19842 said:**
>  I need an older version of Blender

What specific version of Blender?

I currently use multiple old versions of Blender on Xubuntu 18.04.  If I'm remembering right, Blender 2.58a and later should "just work", i.e. you just download the binary tarball from your link and unpack it.

> and not just blender (though i really need older version) but other old software versions too ? !

In general?  It often *can* be done, but you might have some work in store.  In my experience doing this, old software versions may need to be recompiled for the newer OS, and this sometimes doesn't work without modifying the source code.  You might also need to compile older versions of dependencies libs.

What other old software versions are you looking to run?

---

