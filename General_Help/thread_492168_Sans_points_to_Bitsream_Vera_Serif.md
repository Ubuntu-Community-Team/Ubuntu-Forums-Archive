---
title: "Sans points to Bitsream Vera Serif"
date: 2007-07-04
forum: General Help
---

### Post by toxin on 2007-07-04
I can't find a solution to this problem. In my system Sans is an alias for Bitstream Vera **Serif**, instead of Bitstream Vera Sans.
Strange is that the file /etc/fonts/local.conf seems correct:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>Serif</family>
        <prefer>
            <family>Bitstream Vera Serif</family>
        </prefer>
    </alias>
    <alias>
        <family>Sans</family>
        <prefer>
            <family>Bitstream Vera Sans</family>
        </prefer>
    </alias>
    <alias>
        <family>Monospace</family>
        <prefer>
            <family>Bitstream Vera Sans Mono</family>
        </prefer>
    </alias>
</fontconfig>

```

What's wrong?

---

### Post by moore.bryan on 2007-07-04
*have you run fontconfig?*

---

### Post by toxin on 2007-07-04
Hi Bryan, thank you for your reply.

> **moore.bryan said:**
> *have you run fontconfig?*

Do you mean "sudo dpkg-reconfigure fontconfig"? Yes, several times. 
Actually the problem begun when I tried one of those howto to improve font rendering. Since then, I couldn't restore the initial behaviour.

---

### Post by moore.bryan on 2007-07-04
> **toxin said:**
> I tried one of those howto to improve font rendering.
*which one?  i checked my /etc/fonts/font.conf file and there's no part of it that looks like what you have... strange.*

---

### Post by toxin on 2007-07-04
> **moore.bryan said:**
> *which one?  i checked my /etc/fonts/font.conf file and there's no part of it that looks like what you have... strange.*

This one: [http://ubuntuforums.org/showthread.php?t=343670&highlight=improve+font](http://ubuntuforums.org/showthread.php?t=343670&highlight=improve+font)

The file is **local.conf**, not font.conf.

---

### Post by moore.bryan on 2007-07-04
*strange... that's the same one i followed and also don't have a local.conf file...*

---

### Post by toxin on 2007-07-05
> **moore.bryan said:**
> *strange... that's the same one i followed and also don't have a local.conf file...*

I deleted that file, did a fresh fontconfig, rebooted (since I switched from beryl to compiz fusion gnome is affected by the black screen of death and I can't kill X, switch user or logout & re-login), but Sans still points to Vera Serif...

By the way, when did linux become so unpredictable? I'm trying to return to it after a 5 year absence (no home PC) and I started using it 10 years ago. You had no rotating cube then, and even gnome and kde were little more than toys. If you had to browse your filesystem you launched an xterm. You had to set private servers for most internet services, e.g. you had to set up sendmail, fetchmail and then you could use an email client to manage your local mailbox. 
But hey guys, if you had a problem you eventually managed to understand and solve it. Maybe you had to go through a bunch of guides and howtos but eventually you learned how things work and could make them work. Nowadays you're often stuck with things that simply don't work. Guides are all click here, click there, paste these commands in your terminal but you can't get any abstraction. Maybe it's just that I'm not familiar with all this new stuff yet. But at first sight it seems that linux has become unpredictable. Alas...

---

### Post by mcduck on 2007-07-05
> **toxin said:**
> I deleted that file, did a fresh fontconfig, rebooted (since I switched from beryl to compiz fusion gnome is affected by the black screen of death and I can't kill X, switch user or logout & re-login), but Sans still points to Vera Serif...

By the way, when did linux become so unpredictable? I'm trying to return to it after a 5 year absence (no home PC) and I started using it 10 years ago. You had no rotating cube then, and even gnome and kde were little more than toys. If you had to browse your filesystem you launched an xterm. You had to set private servers for most internet services, e.g. you had to set up sendmail, fetchmail and then you could use an email client to manage your local mailbox. 
But hey guys, if you had a problem you eventually managed to understand and solve it. Maybe you had to go through a bunch of guides and howtos but eventually you learned how things work and could make them work. Nowadays you're often stuck with things that simply don't work. Guides are all click here, click there, paste these commands in your terminal but you can't get any abstraction. Maybe it's just that I'm not familiar with all this new stuff yet. But at first sight it seems that linux has become unpredictable. Alas...

Are you sure 'sans' and 'serif' are not just symlinks inside /usr/share/fonts? In that case you could just remove them and create new ones pointung to whatever font you want..

---

### Post by moore.bryan on 2007-07-05
[i]your issue intrigues me, so i checked my own /etc/fonts/font.config file and found a very interesting line:
```
<!--
  Accept deprecated 'sans' alias, replacing it with 'sans-serif'
-->
        <match target="pattern">
                <test qual="any" name="family">
                        <string>sans</string>
                </test>
                <edit name="family" mode="assign">
                        <string>sans-serif</string>
                </edit>
        </match>

```
now, i'm not 100% sure what this means, but it sounds as though the sans alias has been replaced.
> **toxin said:**
> By the way, when did linux become so unpredictable?
i think linux has always been somewhat unpredictable... that's what draws a lot of people to it.
> **toxin said:**
> I'm trying to return to it after a 5 year absence (no home PC) and I started using it 10 years ago. You had no rotating cube then, and even gnome and kde were little more than toys. If you had to browse your filesystem you launched an xterm. You had to set private servers for most internet services, e.g. you had to set up sendmail, fetchmail and then you could use an email client to manage your local mailbox.
i think part of the unpredictability comes from all the added things.  once something becomes more complex, it's just that: more complex.
> **toxin said:**
>  But hey guys, if you had a problem you eventually managed to understand and solve it. Maybe you had to go through a bunch of guides and howtos but eventually you learned how things work and could make them work. Nowadays you're often stuck with things that simply don't work.
i personally think this goes straight to my point above about complexity.  everyone wants linux to do a-through-z, so it naturally begins to have some hardships.
> **toxin said:**
> Guides are all click here, click there, paste these commands in your terminal but you can't get any abstraction. Maybe it's just that I'm not familiar with all this new stuff yet. But at first sight it seems that linux has become unpredictable. Alas...
i think this is comes from the newer users who want an os that's not microsoft and see linux as a more affordable option than mac.  they're not coming to linux to learn, just to use.  this isn't a slight against those users; they're using linux as an os, not as a playtoy or learning tool.[/i]

---

### Post by toxin on 2007-07-06
**@mcduck**

Nope :(

```

$ sudo find / -type l -iname sans*
$ 

```

**@moore.bryan**

Yes, that code replaces the sans string, which is deprecated, with sans-serif. The problem is that a lot of themes use Sans (uppercase, I don't know if it's case sensitive) and when they are displayed with Serif they suck. Of course I can edit them individually and point to Vera Sans. But it's really annoying that I can't manage to fix this :(

---

### Post by moore.bryan on 2007-07-06
> **@moore.bryan**
Yes, that code replaces the sans string, which is deprecated, with sans-serif. The problem is that a lot of themes use Sans (uppercase, I don't know if it's case sensitive) and when they are displayed with Serif they suck. Of course I can edit them individually and point to Vera Sans. But it's really annoying that I can't manage to fix this :(
*linux is entirely case-sensitive, so that might be it...*

---

### Post by yorkie on 2007-07-06
Hi had the same problem I found this installed it and it worked
You need to enable the "multiverse" repository in Synaptic and then install the msttcorefonts package.
hope it works for you

---

### Post by toxin on 2007-07-07
> **yorkie said:**
> Hi had the same problem I found this installed it and it worked
You need to enable the "multiverse" repository in Synaptic and then install the msttcorefonts package.
hope it works for you

Hi, I had that package already. I tried to uninstall and then reinstall it but nothing changed.
Damn, this is really pissing me off :evil:

---

