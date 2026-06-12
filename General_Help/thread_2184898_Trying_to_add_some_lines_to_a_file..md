---
title: "Trying to add some lines to a file."
date: 2013-10-31
forum: General Help
---

### Post by bonelifer on 2013-10-31
I know I need to find this line:
```
<a href="tv/recorded"><?php echo t('Recorded Programs') ?></a>
```

Then add these two lines underneath that line, each on it's own line

```
&nbsp; | &nbsp;
<a href="episode"><?php echo t('TV Episodes') ?></a>
```


I know SED would be the way to do so, but I have yet to find an example that I understand. Could someone please provide me with the proper sed statement to add to a bash script to automate this. I have to re-add these after each software update and this would make it easier.

---

### Post by steeldriver on 2013-10-31
Handling HTML/PHP with sed is always a PITA - but it would be hard to come up with a more pathological example than that (double quotes AND single quotes in the pattern, as well as the usual special characters like / and ?). You will need to escape or bracket (turn into literal character ranges) those - which you do where is partly a matter of style. I *think* that these work:

1) using the sed append (a) command

```

$ sed "[COLOR=#0000cd]**/**[/COLOR]<a href=[COLOR=#ff0000]**\**[/COLOR]"tv[COLOR=#ff0000]**\**[/COLOR]/recorded[COLOR=#ff0000]**\**[/COLOR]"><[COLOR=#ff0000]**[**[/COLOR]?[COLOR=#ff0000]**]**[/COLOR]php echo t([COLOR=#ff0000][/COLOR]'[COLOR=#ff0000][/COLOR]Recorded Programs[COLOR=#ff0000][/COLOR]'[COLOR=#ff0000][/COLOR]) [COLOR=#ff0000]**[**[/COLOR]?[COLOR=#ff0000]**]**[/COLOR]><[COLOR=#ff0000]**\**[/COLOR]/a>[COLOR=#0000cd]**/a\**[/COLOR]your first new line[COLOR=#0000cd]**\n**[/COLOR]your second new line" yourfile

```

2) with the more common sed substitute (s) command (can get rid of the escapes of the slashes by using a different character such as | as the separator) 

```

$ sed "[COLOR=#0000cd]**s|**[/COLOR]<a href=[COLOR=#ff0000]**\**[/COLOR]"tv/recorded[COLOR=#ff0000]**\**[/COLOR]"><[COLOR=#ff0000]**[**[/COLOR]?[COLOR=#ff0000]**]**[/COLOR]php echo t([COLOR=#ff0000][/COLOR]'[COLOR=#ff0000][/COLOR]Recorded Programs[COLOR=#ff0000][/COLOR]'[COLOR=#ff0000][/COLOR]) [COLOR=#ff0000]**[**[/COLOR]?[COLOR=#ff0000]**]**[/COLOR]></a>[COLOR=#0000cd]**|&\n**[/COLOR]your first new line[COLOR=#0000cd]**\n**[/COLOR]your second new line[COLOR=#0000ff]**|**[/COLOR]" yourfile

```

---

### Post by bonelifer on 2013-10-31
I was able to get the second one to "work", but it just spits the content out to the console. How would I have it write it back to the file?

```
sed "s|<a href=\"tv/recorded\"><[?]php echo t('Recorded Programs') [?]></a>|&\n\&nbsp\; \| \&nbsp\;\n<a href=\"episode\"><[?]php echo t('TV Episodes') [?]></a>|" header.php
```

---

### Post by Vaphell on 2013-10-31
add **-i** switch for in-place modification

---

### Post by bonelifer on 2013-10-31
> **Vaphell said:**
> add **-i** switch for in-place modification

Thanks. I swear I looked at the online documentation for sed and didn't see that.  I guess new stuff is often overwhelming at first.

---

