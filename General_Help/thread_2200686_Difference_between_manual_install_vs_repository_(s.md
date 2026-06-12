---
title: "Difference between manual install vs repository (software)"
date: 2014-01-20
forum: General Help
---

### Post by samwillc on 2014-01-20
Hi,

I wanted to use sublime text 2 on ubuntu 12.04 seeing as I bought a license and already use it on OSX. Now I can find a few ways to do this:

[http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html](http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html)

and

[http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/](http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/)

or even:

[http://sublime-text-unofficial-documentation.readthedocs.org/en/sublime-text-2/getting_started/install.html#linux](http://sublime-text-unofficial-documentation.readthedocs.org/en/sublime-text-2/getting_started/install.html#linux)

So what does downloading it via the repository actually do, how do I know what steps are being taken via this route? I want to be able to:

1) Right click a file and open wih sublime text 2
2) Launch sublime text 2 from the unity launcher
3) Use subl /path/to/file in terminal to quickly open/create files

Is there a preferred way to install this so that I am sure the above three things will work?

Thanks for any input.

Sam.

---

### Post by raptir on 2014-01-20
The major difference is that installing from a repository allows for automatic updates.. Usually I recommend using a repository, but in the case of Sublime Text 2 it appears that they distribute the application as a pre-compiled binary, so the installation should not be too terribly difficult. The risk of a non-official repository (like the webupd8 one you've linked) is that it has the potential to not be legitimate (though webupd8 is reputable) or not stay up to date (though it seems to be up to date in this case). The repository will be easier and will give you automatic updates as long as the repository is kept up to date. I would either use the webupd8 repo or the instructions in the technoreply link. Both will give you the three things you're asking for. If you use the technoreply instructions you'll just need to download and unpack the new version to update each time, but you'll be guaranteed to be up to date.

---

### Post by samwillc on 2014-01-22
@raptir, thanks for the info :)

---

