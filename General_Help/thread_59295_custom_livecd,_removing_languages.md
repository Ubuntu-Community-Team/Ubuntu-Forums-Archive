---
title: "custom livecd, removing languages"
date: 2005-08-23
forum: General Help
---

### Post by jdh2358 on 2005-08-23
I want to remove the non-english languages frm my custom live cd.  I do the following

> apt-get remove language-pack-pt-base language-pack-es-base language-pack-zh-base language-pack-de-base language-pack-ja-base language-pack-ru-base language-pack-ca-base language-pack-ar-base language-pack-bn-base language-pack-hi-base language-pack-zh language-pack-ru language-pack-pt language-pack-ja language-pack-hi language-pack-fr language-pack-es language-pack-de language-pack-ca language-pack-bn language-pack-ar

The problem is that for each package that is removed, ubuntu reconfigures it's locales

Generation complete.
Removing language-pack-bn-base ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done

and *lots more* like this

This takes a really long time.  Is there a way to remove these and have the locales regenerated only once, at the end?

Thanks!
JDH

---

### Post by TheeMahn2003 on 2006-09-20
> **jdh2358 said:**
> I want to remove the non-english languages frm my custom live cd.  I do the following

> apt-get remove language-pack-pt-base language-pack-es-base language-pack-zh-base language-pack-de-base language-pack-ja-base language-pack-ru-base language-pack-ca-base language-pack-ar-base language-pack-bn-base language-pack-hi-base language-pack-zh language-pack-ru language-pack-pt language-pack-ja language-pack-hi language-pack-fr language-pack-es language-pack-de language-pack-ca language-pack-bn language-pack-ar

The problem is that for each package that is removed, ubuntu reconfigures it's locales

Generation complete.
Removing language-pack-bn-base ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done

and *lots more* like this

This takes a really long time.  Is there a way to remove these and have the locales regenerated only once, at the end?

Thanks!
JDH

Have you considered using [reconstructor]("http://reconstructor.aperantis.com/")?  I have been re-writing it in python to add the removal of language packs minus english of course :)  Perhaps you should try 
```
dpkg -P language-pack-pt-base language-pack-es-base language-pack-zh-base language-pack-de-base language-pack-ja-base language-pack-ru-base language-pack-ca-base language-pack-ar-base language-pack-bn-base language-pack-hi-base language-pack-zh language-pack-ru language-pack-pt language-pack-ja language-pack-hi language-pack-fr language-pack-es language-pack-de language-pack-ca language-pack-bn language-pack-ar
```
Actually I think the base packages is all that needs to be removed the others will be selected automatically.  If you are going to do it in the way you have add the --purge to your apt-get remove.  I have uploaded my modified version attached below.  I have also added a test iso (not in available in reconstructor that shows up on the last page to allow you to test it before burning, I plan on adding additional features as well let me know what you think.

---

