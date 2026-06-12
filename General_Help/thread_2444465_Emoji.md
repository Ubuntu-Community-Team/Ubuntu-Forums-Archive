---
title: "Emoji"
date: 2020-05-30
forum: General Help
---

### Post by yegnal on 2020-05-30
Found it interesting that I could customize my bash prompt, and I was ultimately able to insert the US flag at the start of the prompt by editing ~.bashrc and inserting   $'\UFE4E6  '

Question concerns the unicode for the flag which I only found by accident, most listings are NOT the flag.  



Is there a particular reference I should consider a resource for Bash compatible emoji unicodes in Linux, in my case Ubuntu ?

I tried researching but come up blank.  
I'm thinking this code I found is part of some standardized convention, I just would love to know where there's a COMPLETE list, not just of unicodes but specifically the ones belonging to this particular collection which includes the one I found.

Seems unicode codes are a system of organized chaos.

---

### Post by DuckHook on 2020-05-30
While Linux allows for customization to a level that proprietary OSes can only dream of, this does not mean that such customizations are in your best long-term interest. My standard advice to all users is to keep your base system as close to its default state as possible. This will save you a world of hurt at each update and you will thank yourself for such self-discipline at release-upgrade time. Customizations inside a VM or a container are an entirely different matter. Because we have the luxury of rolling back to good snapshots with these technologies, customizing to the point of system breakage is not a problem.

Unicode is a largely useful but occasionally mixed blessing. It allows us to access a wealth of characters and is especially useful for glyph-based languages, but it also leads to incompatibility between distros, releases and sometimes even flavours. When it comes to the most basic elements of an OS like the CLI shell, the "lowest common denominator" is not a pejorative.

I wrote [this]("https://ubuntuforums.org/showthread.php?t=2416537&p=13851015#post13851015") tutorial to show an easy method for character insertion within Ubuntu. It contains a short section on Unicode with further useful links therein.

The Unicode table does possess a certain logic, but it is difficult to catalogue in any linear fashion something as amorphous as the loosely interlinked and wackily cross&#8209;connected elements of language.

Again, tread carefully with this newfound power.

---

### Post by CatKiller on 2020-05-30
> **yegnal said:**
> Is there a particular reference I should consider a resource for Bash compatible emoji unicodes in Linux, in my case Ubuntu ?

I tried researching but come up blank.  
I'm thinking this code I found is part of some standardized convention, I just would love to know where there's a COMPLETE list, not just of unicodes but specifically the ones belonging to this particular collection which includes the one I found.

[https://unicode.org/charts/](https://unicode.org/charts/)
[https://emojipedia.org/](https://emojipedia.org/)

There's also the character map for each desktop environment, and KDE has an emoji picker that you can launch with the Meta-. keyboard shortcut in Kubuntu 20.04.

It takes a little while for support for newer encodings to roll out to applications when a new version of Unicode is released. To test a particular encoding once you've found it you can use, for example,
```
echo -e '\Ufe4e6'
```

Some Unicode encodings use Zero Width Joiners (or just mash them together) to combine multiple other encodings into a new character. For example some country flags are created by combining the country-code encoding Regional Indicator Symbols, to make the codepages more general and less unwieldy. Benin's flag shows as &#127463;&#127471; in Kate, but ```
echo -e '\U1f1e7\U1f1ef'
``` is displayed as &#127463; &#127471;in Konsole.

---

### Post by Impavidus on 2020-05-31
Bash doesn't care whether your characters are latin, chinese or emoji. It knows a few special characters, all of which are ascii, and considers everything else a letter. The important part is whether your terminal and fonts support your emojis.

---

