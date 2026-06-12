---
title: "Locales problems"
date: 2006-10-19
forum: General Help
---

### Post by petter1 on 2006-10-19
I'm having some problems with my locales. I think its related to a disk problem i had some time ago. When trying to reconfigure locales i get this error:

> 001  	pettern@pettern-ubuntu:~$ sudo dpkg-reconfigure locales 
002  	Password: 
003  	perl: warning: Setting locale failed. 
004  	perl: warning: Please check that your locale settings: 
005  	        LANGUAGE = "no_NO.UTF-8", 
006  	        LC_ALL = (unset), 
007  	        LANG = "no_NO.UTF-8" 
008  	    are supported and installed on your system. 
009  	perl: warning: Falling back to the standard locale ("C"). 
010  	locale: Cannot set LC_ALL to default locale: No such file or directory 
011  	Generating locales... 
012  	  en_AU.UTF-8... up-to-date 
013  	  en_BW.UTF-8... up-to-date 
014  	  en_CA.UTF-8... up-to-date 
015  	  en_DK.UTF-8... up-to-date 
016  	  en_GB.UTF-8... up-to-date 
017  	  en_HK.UTF-8... up-to-date 
018  	  en_IE.UTF-8... up-to-date 
019  	  en_IN.UTF-8... up-to-date 
020  	  en_NZ.UTF-8... up-to-date 
021  	  en_PH.UTF-8... up-to-date 
022  	  en_SG.UTF-8... cannot write output files to `/usr/lib/locale/en_SG.utf8/': Permission denied 
023  	failed 
024  	  en_US.UTF-8... cannot write output files to `/usr/lib/locale/en_US.utf8/': Permission denied 
025  	failed 
026  	  en_ZA.UTF-8... cannot write output files to `/usr/lib/locale/en_ZA.utf8/': Permission denied 
027  	failed 
028  	  en_ZW.UTF-8... pettern@pettern-ubuntu:~$ cannot write output files to `/usr/lib/locale/en_ZW.utf8/': Permission denied 
029  	failed 
030  	  no_NO.UTF-8... up-to-date 
031  	Generation complete. 
032  	Current default timezone: 'Europe/Oslo'. 
033  	Local time is now:      Thu Oct 19 21:02:53 CEST 2006. 
034  	Universal Time is now:  Thu Oct 19 19:02:53 UTC 2006. 
035  	Run 'tzconfig' if you wish to change it.

Is there any way to reset all configs related to locales or in some other way fix this problem?

---

