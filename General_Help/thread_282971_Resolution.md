---
title: "Resolution"
date: 2006-10-23
forum: General Help
---

### Post by katana6434 on 2006-10-23
Hi

In my windows installxation I can get a resolution of 1600x1200, yet the maximun in Ubuntu is 1280x1024.

My graphics card in a Nvidia 7800GTX and I have the nvidia drivers installed.  Is there anyway that I can use this resolution.  

Cheers

---

### Post by jimmyk on 2006-10-23
If you have an LCD monitor this might help. It worked for me anyway :D 

[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration]("https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration")

---

### Post by katana6434 on 2006-10-23
Cheers for the reply.

Unfortunatly it did not work, or more likely I did something wrong.  :-k 

I followed the guide and done what it suggested.  When I restarted X I received error messages in a blue screen asking if I wanted to look at the logs.  Basically it said the following:

```
Parse error on line 125 of section Screen in file /etc/X11/xorg.conf
"1600 x 1200" is not a valid keyword in this section
```

What have I done wrong?  I have a 19" CRT monitor if it helps.  An AOC Spectrum 9KLr.

Luckily I had made a backup of the xorg.conf file so I could restart X.  I have attached the bad config file if it helps.

Cheers is advance.
](*,)

---

### Post by sefs on 2006-10-23
you have
```

        Modes      1600x1200_75.00 "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

```
 
try surrounding all the 1600x1200_75.00 with double quotes.

i.e

```

        Modes      "1600x1200_75.00" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

```

What i am not sure about though is if the other resolutions on the line need to have the frequency appended also.  But try adding the quotes and give it a shot.  Remember to do it for all the lines on which you have your resolution.

Thanks.

> **katana6434 said:**
> Cheers for the reply.

Unfortunatly it did not work, or more likely I did something wrong.  :-k 

I followed the guide and done what it suggested.  When I restarted X I received error messages in a blue screen asking if I wanted to look at the logs.  Basically it said the following:

```
Parse error on line 125 of section Screen in file /etc/X11/xorg.conf
"1600 x 1200" is not a valid keyword in this section
```

What have I done wrong?  I have a 19" CRT monitor if it helps.  An AOC Spectrum 9KLr.

Luckily I had made a backup of the xorg.conf file so I could restart X.  I have attached the bad config file if it helps.

Cheers is advance.
](*,)

---

### Post by katana6434 on 2006-10-23
Thanks a lot.

That got it working.  I had to take out the refresh bit at the end.

I could have sworn that I put the quotes in first time round.  Amazing what you think you have done when you hadn't.  :rolleyes: 

Cheers

:mrgreen:

---

