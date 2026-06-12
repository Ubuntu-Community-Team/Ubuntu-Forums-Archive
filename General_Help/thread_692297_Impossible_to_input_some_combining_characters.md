---
title: "Impossible to input some combining characters"
date: 2008-02-09
forum: General Help
---

### Post by LordOfThePigs on 2008-02-09
Hello everyone,

I'm currently studying chinese, so I was trying to tweak my keyboard layout to be able to type pinyin with tone marks. I use a swiss-french keyboard, so the accute (') accent and the grave(`) accent were already there. I just needed to be able to type macron(¯) and caron(&#711;) accents.

I have managed to create a new keyboard layout with xkb which replaces the tilde and circumflex by the caron and macron respectively, and to make that keyboard layout appear in the keyboard administration applet. It turns out that everything works... almost.

My problem is not actually with the keyboard, but with the fact that ubuntu seems to filter which characters it will display and which characters it will not. 

The symptoms are the following. I can now type &#275;&#257;&#299;&#333;&#363; to my hearts content, and &#283; works. However, if I try to type &#462;&#464;&#466;&#468;, I get a system beep and no character is printed.

Now here are the few things I found out about my problem: 

1). By looking at the block of letters around it, &#283; seems to be a valid eastern European character, while all of &#462;&#464;&#466;&#468; are only used as third tone Chinese letters. This information can be confirmed by looking at the character map applet.

2). X does produce a keypress event with the correct character for each of the non-working &#462;&#464;&#466;&#468;. Here's the output of xev when I press &#711; then a:
```

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x13a, subw 0x0, time 4294178779, (107,347), root:(769,401),
    state 0x0, keycode 21 (keysym 0xfe5a, dead_caron), same_screen YES,
    XLookupString gives 2 bytes: (cb 87) "&#711;"
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x13a, subw 0x0, time 4294178870, (107,347), root:(769,401),
    state 0x0, keycode 21 (keysym 0xfe5a, dead_caron), same_screen YES,
    XLookupString gives 2 bytes: (cb 87) "&#711;"
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x13a, subw 0x0, time 4294179001, (107,347), root:(769,401),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: True

KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x13a, subw 0x0, time 4294179001, (107,347), root:(769,401),
    state 0x0, keycode 0 (keysym 0x10001ce, U01CE), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 2 bytes: (c7 8e) "&#462;"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x13a, subw 0x0, time 4294179086, (107,347), root:(769,401),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

```
which can be summarized like this
```

KeyPress: "&#711;"
KeyRelease: "&#711;"
KeyPress: "a"
KeyPress: "&#462;"
KeyRelease: "a"

```

as you can see the correct keypress event is generated. I get the same kind of response for each &#711; + letter combination I push, but only &#283; ultimately makes it all the way to the screen.

I have tried with SCIM both installed and uninstalled, and the problem occurs in both cases.

I suspect those characters I want to display are beeing filtered somewhere in ubuntu after X has fired the keypress event (based on the locale I use maybe? en_US.UTF-8).

Does anybody have an idea where those characters get lost? Until I find out, I'm pretty much forced to keep using windows to type my pinyin... which bugs me a little.

Thanks for your help

---

### Post by LordOfThePigs on 2008-02-14
From the lack of response, I'm guessing that this is bug. I'll submit this to launchpad if I don't get any answer for a few more days.

---

### Post by brtkrbzhnv on 2008-03-16
> **LordOfThePigs said:**
> From the lack of response, I'm guessing that this is bug. I'll submit this to launchpad if I don't get any answer for a few more days.
Any updates? I couldn't find anything on [https://bugs.launchpad.net/projects/?text=caron](https://bugs.launchpad.net/projects/?text=caron). I'd really like to be able to type &#462; without ctrl+v.

---

### Post by Codexus on 2008-03-17
n&#464;menh&#462;o :)

I encountered the same problem today. The config is OK on the xkbd side, it works well within a simple program like xterm or even with many apps when started from a "naked" X environment but not in a full gnome or KDE environment. I guess those use their own dead keys system.

Anyway it's not like I absolutely wanted dead keys for that task and since it's unlikely that I'll mix french and pinyin very often I just made a second keyboard configuration with all the pinyin accents and I can just switch between them.

Here's my pinyin config. It might save you some typing and the trouble of finding out the codes for those characters that don't have a named constant.

It's meant to be appended to the us keyboard layout file but it shouldn't be hard to modify for other layouts.

```

partial alphanumeric_keys
xkb_symbols "pinyin" {
    name[Group1]= "U.S. English - Pinyin";

    include "us(basic)"

    key <AC01> { [         a,          A,        aacute,           agrave ] };
    key <AB01> { [         z,          Z,        0x10001ce,        amacron ] };

    key <AD03> { [         e,          E,        eacute,           egrave ] };
    key <AC03> { [         d,          D,        ecaron,           emacron ] };

    key <AD05> { [         t,          T,        udiaeresis ] };
    key <AD06> { [         y,          Y,        0x10001d8,        0x10001dc ] };
    key <AC06> { [         h,          H,        0x10001da,        0x10001d6 ] };

    key <AD07> { [         u,          U,        uacute,           ugrave ] };
    key <AC07> { [         j,          J,        0x10001d4,        umacron ] };

    key <AD08> { [         i,          I,        iacute,           igrave ] };
    key <AC08> { [         k,          K,        0x10001d0,      imacron ] };

    key <AD09> { [         o,          O,        oacute,      ograve ] };
    key <AC09> { [         l,          L,        ocaron,      omacron ] };


    include "level3(ralt_switch)"
};

```

---

