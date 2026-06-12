---
title: "Font issue in terminal"
date: 2017-09-12
forum: General Help
---

### Post by Asiful_Nobel on 2017-09-12
I have a program that outputs Bangla in the terminal. But unfortunately, the output is not displayed properly by gnome-terminal in Ubuntu 16.04 LTS. 


The output should look like this:

```
&#2438;&#2474;&#2472;&#2494;&#2470;&#2503;&#2480; &#2470;&#2507;&#2453;&#2494;&#2472; &#2453;&#2476;&#2503; &#2454;&#2507;&#2482;&#2494; &#2469;&#2494;&#2453;&#2476;&#2503;?
```

Instead it looks like this with a Ubuntu Mono font:


[IMG]https://i.stack.imgur.com/M6Vgd.png[/IMG]


Further it looks like this with Kalpurush font that supports Bangla: 

[IMG]https://i.stack.imgur.com/Zmig1.png[/IMG]


I have checked with xfd to see if the bangla character range is available in the two fonts. As expected, Ubuntu Mono had empty boxes in the character range, whereas Kalpurush had correct representational symbols.


Additionally, locale is set to UTF-8. `locale` output:

    ```

    LANG=en_US.utf8
    LANGUAGE=
    LC_CTYPE=en_US.UTF-8
    LC_NUMERIC=en_GB.UTF-8
    LC_TIME=en_GB.UTF-8
    LC_COLLATE="en_US.utf8"
    LC_MONETARY=en_GB.UTF-8
    LC_MESSAGES="en_US.utf8"
    LC_PAPER=en_GB.UTF-8
    LC_NAME=en_GB.UTF-8
    LC_ADDRESS=en_GB.UTF-8
    LC_TELEPHONE=en_GB.UTF-8
    LC_MEASUREMENT=en_GB.UTF-8
    LC_IDENTIFICATION=en_GB.UTF-8
    LC_ALL=

```

I have also tried with Bangla locale, but it did not work.
Moreover, Terminal character encoding is also set to Unicode(UTF-8). Yet, nothing worked.

So, then I tried out Guake Terminal Emulator. But it did not work either.

Now what can I do more to fix this issue? :sad:

---

### Post by BenginM on 2017-09-12
Try to install fonts-beng .

[https://askubuntu.com/questions/954990/bangla-font-issue-in-terminal](https://askubuntu.com/questions/954990/bangla-font-issue-in-terminal)

I was goin' to suggest KDE Konsole terminal next, but someone already bet me to it.

and this is not a bug or an issue , it a missing feature/support. it's also the case for Arabic and Hebrew bidi . feel free to suggest it to the gnome terminal devs upstream.

other than KDE Konsole, there is Mlterm .

---

