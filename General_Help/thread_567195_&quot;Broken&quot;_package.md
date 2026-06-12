---
title: "&quot;Broken&quot; package"
date: 2007-10-04
forum: General Help
---

### Post by Frijolie on 2007-10-04
I was running the Update Manager today and got an error that "I have '1' broken package" and that I was supposed to run the "Broken" filter to fix it.

I went to Synaptic and ran the 'broken' filter to try and reinstall the offending package but still no luck. I have also done

```

sudo apt-get -f install 

```

and 

```

sudo dpkg --configure -a

```


None have been successful and this is the error it's giving me:

```

E: /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb: trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0

```

```

brian@brian-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on gimp (= 2.4.0~rc3-1ubuntu5); however:
  Version of gimp on system is 2.4.0~rc3-1ubuntu4.
dpkg: error processing gimp-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gimp-python

```

where/what do I go/do next?

---

### Post by ThrobbingBrain66 on 2007-10-04
[http://ubuntuforums.org/showthread.php?t=567185](http://ubuntuforums.org/showthread.php?t=567185)

Check out the thread above.  It's always a good idea to check out the Development forum when running a development release.  Chances are other people are having the same issues.

---

### Post by Frijolie on 2007-10-04
Thanks, missed that one... 

Thanks for the tips on the "development" forum, will do for next time

---

