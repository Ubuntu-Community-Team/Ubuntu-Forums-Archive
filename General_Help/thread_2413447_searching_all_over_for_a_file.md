---
title: "searching all over for a file"
date: 2019-02-25
forum: General Help
---

### Post by Skaperen on 2019-02-25
i want to search a stack of hard drives that has millions of mostly largish files (some have upwards of 5GB but some are smaller than 4K). but one thing plays to my advantage: the string i need to search for is within the first 512 bytes of whatever file it is in.  i could not find an option on grep that would confine the search to just a small part of the file.  does anyone have any ideas?

---

### Post by HermanAB on 2019-02-26
Linux grep is remarkably fast.  Scanning everything will by much quicker than asking for help to make it faster...

---

### Post by Holger_Gehrke on 2019-02-26
Just a rough sketch of a way to do it: use 'find' with '-exec' to get all file names and execute a script. The script would look something like
```

if dd if="$1" bs=512 count=1|grep 'searchstring' ; then echo $1; fi

```

Holger

---

### Post by dragonfly41 on 2019-02-26
ripgrep claims it is speedier in benchmarks ... [https://github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)

---

### Post by Skaperen on 2019-02-27
> **HermanAB said:**
> Linux grep is remarkably fast.  Scanning everything will by much quicker than asking for help to make it faster...

perhaps so.  but i cannot leave the stack of drives on there for the many hours it will take.

---

### Post by dragonfly41 on 2019-02-27
I suggest that you approach the author (burntsushi) of ripgrep to see how the search can be restricted to first 512 bytes.

[https://www.reddit.com/r/rust/comments/9dxewq/ripgrep_0100_released_pcre2_and_multiline_support/](https://www.reddit.com/r/rust/comments/9dxewq/ripgrep_0100_released_pcre2_and_multiline_support/)

---

### Post by Skaperen on 2019-02-27
> **Holger_Gehrke said:**
> Just a rough sketch of a way to do it: use 'find' with '-exec' to get all file names and execute a script. The script would look something like
```

if dd if="$1" bs=512 count=1|grep 'searchstring' ; then echo $1; fi

```

Holger
i did it in a slightly different way, but this basically worked.
```

(find ... -print|while read f;do if dd if="$f" bs=512 count=1|grep -q 'findme';then echo "x$f"|cut -c2-;fi;done)

```

---

