---
title: "Compile/Install App without losing original"
date: 2006-08-09
forum: General Help
---

### Post by SteveF on 2006-08-09
I'm hoping someone can point me in the right direction (links or knowledge).  I need a newer version of an app (ImageMagick) than Dapper provides.  My thought is to download the code, compile and install it.  But, I prefer to stay with what Ubuntu provides whenever possible and if a newer version becomes available from Ubuntu, I would prefer to install that.

If I download source, compile and install it, does it overwrite what Ubuntu installed, if not does the installed version take precedence in path ordering?  Am I better off removing the Ubuntu version first?  In either case, will I be notified by Ubuntu that a new version is available or will it assume I have a newer version and not notify.  Finally would I need to uninstall the compiled code (I'm hoping the make file has an uninstall option) prior to installing the Ubuntu version?

Thanks for any info,

Steve

---

### Post by taurus on 2006-08-09
If you compile and install it from source, it will not remove the one that you installed with apt-get/aptitude/synaptic unless you install it in the same directory.  Then, it will overwrite the older version.  Therefore, the best way is to remove it with apt-get/aptitude/synaptic first.  Then, compile and install it from source...  You can have two versions of the same app on your machine if you want and depending on your path, it will be executed first if it's in your path first!  For instance, if you install it with apt-get and it goes into /usr/bin while you compile and build it into /usr/local/bin, and your path looks something like /bin:/usr/bin:/usr/local/bin, then the /usr/bin will get executed everytime unless you specify the one from /usr/local/bin...

---

### Post by SteveF on 2006-08-09
Thanks for the response.  I left the Synaptic version and installed the source compiled into /usr/local/bin.  I want to be notified if Ubuntu offers a newer version and then I'll remove the source compiled one.

Steve

---

### Post by taurus on 2006-08-09
That's fine too.  However, I think the one from synaptic will be execute first since I believe /usr/bin is ahead of /usr/local/bin so if you want to use the one in /usr/local/bin, you need to include the whole path or switch the order in your PATH!!!  Including the whole path (or a link to it) is a better choice...

---

### Post by SteveF on 2006-08-09
Thanks for the suggestion.  I checked my path and /usr/local/bin comes before /usr/bin so I'm all set with that.  Kind of weird but probably a cahing thing, the one in /usr/lib/bin would not execute even though the path stated it should.  I opened a new command prompt and it worked.  So I'm guessing that the first command prompt stored a folder list in a cache and thought convert was not in the /usr/local/bin.

Also, as a note to anyone reading this who is going to compile ImageMagick, make sure you have the dev libs installed.  In my case, libjpeg62-dev needed to be installed from Synaptic.  ImageMagick's configure assumed I did not have jpeg support and compiled fine but none of the tools worked on jpeg files.  Including that lib and rerunning configure/make/make install solved the issue.

Since I use mostly jpeg files that's all I looked for, but it is possible other file types have not been compiled in because of missing libs.

Steve

---

