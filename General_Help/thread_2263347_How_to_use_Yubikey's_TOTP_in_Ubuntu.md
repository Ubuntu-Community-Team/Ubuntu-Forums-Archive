---
title: "How to use Yubikey's TOTP in Ubuntu?"
date: 2015-01-31
forum: General Help
---

### Post by markodd on 2015-01-31
[FONT=verdana][SIZE=4][SIZE=2][COLOR=#333333]Yubico's linux support is absolutely horrible, so I need to ask here instead. Sad.
[/COLOR]
[SIZE=2][COLOR=#333333]I already have the "Yubikey Personalization Tool", in which I can write to a configuration slot. I also have the "Python-yubico-tools" installed. I managed to write to slot 2 on my yubikey (challenge response) and after typing "yubikey-totp" in terminal, I do get a 6-digit code. However, the code is wrong and doesn't work.[/COLOR]
[COLOR=#333333]I think the problem is that I'm pasting the code that a specific site (dropbox) gives me incorrectly in the Personalization Tool.[/COLOR]
[/SIZE][COLOR=#333333]Any help would be appreciated.


PS: I'm not sure if this should be in the "Security" section instead. If you think so, please feel free to move it.

EDIT 1:

The font is stupid. I'm trying to change it to the default one, but I've no idea what it is.[/COLOR][/SIZE][/SIZE][/FONT]

---

### Post by ajgreeny on 2015-01-31
[FONT=verdana]Try [SIZE=1]Verdana[/SIZE] size 1 for the font.

As to your main problem; I haven't got a clue.
[/FONT]

---

### Post by Erik1984 on 2015-01-31
This could also explain the wrong codes:

[http://www.yubico.com/wp-content/uploads/2014/02/Yubico-TOTP-Setup.pdf](http://www.yubico.com/wp-content/uploads/2014/02/Yubico-TOTP-Setup.pdf)
> Make sure the system time on the host computer is correct if the system time is off, the time dependent codes will not be valid. Make sure the host computer is set to the correct time, or automatically syncing its internal clock to a valid timekeeping site



Another approach is to generate the TOTP codes from the terminal with [oathtool]("http://packages.ubuntu.com/trusty/oathtool") against the same secret key (in your case from Dropbox) you configured for the Yubikey.
[http://manpages.ubuntu.com/manpages/trusty/man1/oathtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/oathtool.1.html)
This is an example from the manpage that should work for Dropbox (of course with your personal secret key):
```

oathtool --base32 --totp "gr6d 5br7 25s6 vnck v4vl hlao re"

```

If you enter the same secret in the Yubikey tool and oathtool command you can compare the generated TOTP codes.

---

### Post by markodd on 2015-02-01
I think I might have found what the problem was.

In the "Yubikey's personalization tool", the secret key is supposed to be pasted in hex format. According to [this]("https://www.youtube.com/watch?v=VDxJCkx7N4E") youtube video.

I've tried converting it to hex but to no help. Is there any site that you suggest, to convert to hex? I tried several, but they give different results.

About the time: I guess they use the computer's clock, am I correct? How do I know what the "correct" time is? I could be living in Australia, US, China, Germany..

---

### Post by TheFu on 2015-02-01
> **markodd said:**
> I think I might have found what the problem was.

In the "Yubikey's personalization tool", the secret key is supposed to be pasted in hex format. According to [this]("https://www.youtube.com/watch?v=VDxJCkx7N4E") youtube video.

I've tried converting it to hex but to no help. Is there any site that you suggest, to convert to hex? I tried several, but they give different results.

About the time: I guess they use the computer's clock, am I correct? How do I know what the "correct" time is? I could be living in Australia, US, China, Germany..

Security tools will work off UTC. Timezone's are used to display the local time. This problem was solved in the early 1970s for everyone except Microsoft.

**od** is the Linux command to convert between hex/octal/decimal.  According to the manpage, -x is the option.

---

