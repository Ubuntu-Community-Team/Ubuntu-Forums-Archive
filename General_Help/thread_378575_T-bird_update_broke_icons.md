---
title: "T-bird update broke icons"
date: 2007-03-07
forum: General Help
---

### Post by kolinab on 2007-03-07
Hi,

Today's update of Thunderbird to 1.5.0.10 broke some of my Thunderbird icons. My Launcher icon is still the 'better' T-bird icon, but my panel notification button (I use the Moztray biff) and the icon in the window list are both the ugly brown envelope again. 

I tried the [script]("http://www.ubuntuforums.org/showthread.php?t=199193&highlight=take+back+thunderbird") but it returned:

```

kolin@insp:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] n
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Replace the Mozilla Firefox document icon (y/n)? [y] n
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Replace the Mozilla Thunderbird program icon (y/n)? [y] y
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] y
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
Nothing to do here.
kolin@insp:~$ 

```

So now what? This could quite possibly ruin my afternoon. 

Please help me restore order to the universe, starting with my T-bird icon. !! :) 

K

---

### Post by kolinab on 2007-03-07
Sorry folks, I didn't read the instructions properly. I forgot to:

```

$ sudo bash restore_mozilla_icons

```

You need the bash. 

But I got it working again. Thanks for your interest in this short conversation with myself!

K

---

