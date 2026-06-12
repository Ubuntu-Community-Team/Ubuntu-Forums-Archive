---
title: "mrxvt  can't load font"
date: 2008-02-29
forum: General Help
---

### Post by y-lee on 2008-02-29
I installed  [mrxvt]("http://en.wikipedia.org/wiki/Mrxvt") in Dapper using synaptic package manager, After doing so I ran the program and got the following errors:

```
$ mrxvt
mrxvt: can't load font "-taipei-fixed-medium-r-normal--16-150-75-75-c-160-big5-0"
mrxvt: can't load font "-*-*-*-*-*-*-*-*-*-*-c-*-big5-0"
mrxvt: fatal error, aborting...
```

After googling the problem I found some advice on a fedora forum ( if memory serves me right) that fixed this problem. The advice was to add the line **mrxvt*multichar_encoding:noenc** to my .Xdefaults file in my home directory. Looking around I had no .Xdefaults file, so I created one containing only that line and mrxvt now works correctly.

I am posting this to help others who maybe lack my google-fo skills and computer knowledge, as well as to ask if others in more recent distros also have the same issue with installing mrxvt from the repos. Would a couple of you mind trying this. 

Furthermore I would like ask if I should report this as a bug on launchpad despite this happening on Dapper a rather old version of ubuntu. It would seem to me that any program installed using synaptic should also install whatever files are needed to ensure this program works correctly. For the sake of users coming from windows and new to linux, installation from the repos should I feel be as painless as possible.

---

