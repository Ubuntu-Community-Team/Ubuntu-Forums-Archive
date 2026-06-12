---
title: "BIT-ROT on linux too!"
date: 2008-05-29
forum: General Help
---

### Post by slicemaster on 2008-05-29
i am running Ubuntu 8.04 and have been rather impressed by it. however, i am disappointed in some ways because it seems to be subject to all the same problems as windows has with "bit-rot", for those who don't know what bit-rot is, it is when programs leave trash behind after they are removed, this includes configuration files, drivers, file associations, etc. now the reason i bring this up is i have been playing arond with different apps available from the repositories but it seems that when i removethem that they leave behind junk after they are removed and in the case of a reinstall, when i reinstall a given app it uses the same junk that it left when i uninstalled it, that in my case is causeing me big headakes. i don't know if this is the case with all linux apps but from my experience with WINE and a few others, i know that wine has bit-rot issues leaving all it's stuff (windows programs) even though it has been removed.it simply looks as though linux has the same/if not worse bit-rot problems as windows, and i dont want to have to reinstall linux like i do windows every so often because of all the junk thaty gets built up from standard use, so could  would like some tips on how to keep my Linux system clean from garbage many apps leave behind after i decide the apps aren't any good or i dont have need for, and avoid bit-rot.

thanks,

P.S. i am not necessarily complaing about these apps above as being garbage, as a matter of fact i love wine, just had some issues uninstalling a windows program that didn't work correctly, and it wasn't fixed because wine leaves that data on the system even when wine is removed, and it reuses it again when it is reinstalled.

---

### Post by tamoneya on 2008-05-29
one way to decrease the bit-rot is by using the --purge argument.  Try removing the package through terminal with a command like this:```
sudo apt-get remove --purge <package_name>
```That will have the application remove all of its preferences and such.  It should do a better job than just removing through synaptic.

---

### Post by werries on 2008-05-29
there are simple things like,
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
```
or when you uninstall things, there is the "completely remove" option in synaptic, along with the "remove", so use completely remove.
And i know there are --purge functions. 
and sometimes there are partial files left over. so you can use deborphan to clean up leftover stuff sometimes too.
```
sudo apt-get install deborphan
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by lotsofish on 2008-05-29
A lot of the settings for programs are stored in your home directory as a "hidden" directory, starting with a dot (.)

For example, you can remove all the programs and data installed through wine by removing the ~/.wine directory.

---

### Post by slicemaster on 2008-05-30
thanks for the tips...and for all the support... peace.

---

