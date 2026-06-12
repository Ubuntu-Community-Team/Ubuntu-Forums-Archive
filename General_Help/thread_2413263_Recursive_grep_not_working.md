---
title: "Recursive grep not working"
date: 2019-02-23
forum: General Help
---

### Post by Lappert on 2019-02-23
I need to find all specified strings within a set of html files within a directory.

I use:
```
[FONT=monospace][COLOR=#000000]root@mybox:/# grep -i "mystring" /mnt/sdc/9500/9502/*.html[/COLOR]
[COLOR=#B218B2]/mnt/sdc/9500/9502/building.html[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#000000]            [/COLOR][COLOR=#FF5454]**mystring**[/COLOR][COLOR=#000000] by author A  </div>[/COLOR]
[COLOR=#B218B2]/mnt/sdc/9500/9502/toilets.html[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#000000]            [/COLOR][COLOR=#FF5454]**mystring**[/COLOR][COLOR=#000000] by author B  <[/COLOR]/div>
[COLOR=#B218B2]/mnt/sdc/9500/9502/antenna.html[/COLOR][COLOR=#18B2B2]:[/COLOR][COLOR=#000000]            [/COLOR][COLOR=#FF5454]**mystring**[/COLOR][COLOR=#000000] by author C  </div>[/COLOR]
root@mybox:/# 
[/FONT]
```

This works fine. Note the directory 9500 represents a year and 9502 represents a month. In this case it would be Feb. 1995. Each monthly directory has about 70 .html files. So grepping month-to-month works fine.

But I have 25 years to go through, so I would like to do the search by year, not month. So I try this:

```
[FONT=monospace][COLOR=#000000]root@mybox:/# grep -i -r "mystring" /mnt/sdc/9500/*.html 
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]grep: /mnt/sdc/9500/*.html: No such file or directory[/COLOR]
[/FONT][FONT=monospace]root@mybox:/# 
[/FONT]
```



I added the recursive parameter -r and went up one directory to start under the year directory "9500". Note there are no .html files directly under the year; they all are under the monthly subdirectories. I don't think that should matter as the recursive parameter should cause a search in all lower monthly directories (in this case 12 of them). I have verified that each monthly directory has one or more instances of my search string.

But as you can see, grep reports, "[FONT=monospace][COLOR=#000000]grep: /mnt/sdc/9500/*.html: No such file or directory[/COLOR][/FONT]"

I'm at a loss. Any help will be appreciated. Thank you.

---

### Post by Lappert on 2019-02-23
Update: from another post to this forum...

The string I was attempting to use was:
```

[FONT=monospace][COLOR=#000000]root@mybox:/# grep -i -r "mystring" /mnt/sdc/9500/*.html"[/COLOR]
[/FONT]
```

That didn't work. One post suggested I use this construct instead:

```

[FONT=monospace][COLOR=#000000]root@mybox:/mnt/sdc/9500# grep -i -r "mystring" --include="*.html"[/COLOR]
[/FONT]
```

So here it seems the -r parameter is meaningless and the --include does the trick. It worked. But to work I also had to change the present directory to where I wanted to start the search. With the first method, I could start in the root directory, or anywhere.

Using this second method, I was able to retrieve all instances of mystring for the entire year.

The changes are manageable, but it seems inelegant and really doesn't make much sense. Why would -r not work? It is listed in the man page.

Insights? Thanks.

---

### Post by The Cog on 2019-02-23
"/mnt/sdc/9500/*.html" will only list things whos name ends in "html". Probably not any directories, so yes, the -r is useless.
Also, you said there weren't any html files in /mnt/sdc/9500/, they are all in subdirectories under there. You could try:
```
grep -i mystring /mnt/sdc/9500/*/*.html
```
which will work if all the html files are at the same depth. 

This might be another way which will find html files at any depth.
```
grep -i mystring $(find /mnt/sdc/9500 -name "*.html")
```

I have a feeling there may be a (large) limit to the length of the arguments list to a command. This will work when finding any number of files but will be slower because it launches a new grep for each file:
```
find /mnt/sdc/9500 -name '*.html' -exec grep -H mystring '{}' \;
```

---

### Post by Impavidus on 2019-02-23
In your original command[cod[COLOR=#000000]e]grep [/COLOR][FONT=monospace][/FONT]-i "mystring" /mnt/sdc/9500/9502/*.html[/code]the shell will expand the * to match every .html file in the 9500/9502/ directory. That works as expected. In your next command you used ```
[COLOR=#000000]grep [/COLOR][FONT=monospace][/FONT]-i -r "mystring" /mnt/sdc/9500/*.html
```There the shell will expand the * to match every .html file in the 9500/ directory. As there are none, expansion fails and the string including the * character is passed on to grep. grep in turn tried to open the directory 9500/*.html to search for your string in every file in that directory, but failed as that directory doesn't exist and gave you an error message. What went wrong is that you assumed that the * will expand to any path ending in .html, whilst it only expands to one file/directory name ending in .html.

Correct use of the -r option is to provide a directory and grep will then search all files in that directory (including in subdirectories). If no directory is provided (like in your final command), it searches the current directory. The command```
[COLOR=#000000]grep [/COLOR][FONT=monospace][/FONT]-ir "mystring" /mnt/sdc/9500/
```does mostly what you want, but will seach every file.```
grep -ir "mystring" --include="*.html" /mnt/sdc/9500/
```restricts the search to .html files.

Note that the -r option is not meaningless. Without it, grep would search one file (if a file is given) or standard input (if no file is given).

---

### Post by Lappert on 2019-02-23
The Cog ... thank you.

I tried 
```
[FONT=monospace][COLOR=#000000]root@corsair:/mnt/sdc/9500# grep -i "mystring" /mnt/sdc/9500/*/*.html[/COLOR][/FONT]
```

but that only gets me back to where I was before. It's worth knowing as an alternative.

With the find command, I'm just not that familiar with it, but I'll look at it.

---

### Post by Lappert on 2019-02-23
> **Impavidus said:**
> Correct use of the -r option is to provide a directory and grep will then search all files in that directory (including in subdirectories). If no directory is provided (like in your final command), it searches the current directory. The command```
[COLOR=#000000]grep [/COLOR]-ir "mystring" /mnt/sdc/9500/
```does mostly what you want, but will search every file.```
grep -ir "mystring" --include="*.html" /mnt/sdc/9500/
```restricts the search to .html files.

Yes, it seems to do the same as the include usage above, perhaps simpler. This works for an entire year (12 months), but I haven't yet tried it for 25 years. But yearly is fine for my purposes.

Searching every file is not a problem as a typical monthly directory has approx. 70 .html files, and two additional .txt files where I keep the results of the grep search and various regex search/replace modifications.

> Note that the -r option is not meaningless. Without it, grep would search one file (if a file is given) or standard input (if no file is given).

Thank you as well.

---

### Post by The Cog on 2019-02-23
> **Lappert said:**
> The Cog ... thank you.

I tried 
```
[FONT=monospace][COLOR=#000000]root@corsair:/mnt/sdc/9500# grep -i "mystring" /mnt/sdc/9500/*/*.html[/COLOR][/FONT]
```

but that only gets me back to where I was before. It's worth knowing as an alternative.
I'm not sure what your problem is with that. Can you explain what you think the limitation still is?

Edit: We were both typing at the same time.
To search all years, all months, all html files, you should be able to do:
```
grep -i "mystring" /mnt/sdc/*/*/*.html
```
To limit the years (I gather they are all of the form <digit digit 0 0>), this will do year folders 6500-9900:
```
grep -i "mystring" /mnt/sdc/{55..99}00/*/*.html
```

---

### Post by Lappert on 2019-02-23
I didn't mean to imply your solution was a problem. Sorry if that's what you thought. 

On your second solution above, the years directories range from 9300 (1993) to 1800 (2018), Under each one I have monthly directories such as 9301, 9302, ... 9312. 

I just tried ```

[FONT=monospace][COLOR=#000000]grep -i "mystring" /mnt/sdc/{93..99}00/*/*.html[/COLOR]
[/FONT]
```

And it seemed to work very well. I limited the search to {93..99} as {00..18} are not after the 93-99 range. But it's just as easy to make two searches.

Again, thank you.

---

### Post by dragonfly41 on 2019-02-23
I have to search through directories frequently and although grep should meet this requirement
I have now adopted ripgrep in my workflow.  Debian installation described here.

[https://github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)

Another tool I find useful as a GUI is SearchMonkey (Regular expression power search utility). This can search for strings inside files in target directories.

[late edit] However you now seem to have solved your problem.

---

### Post by Lappert on 2019-02-23
Thanks, I'll look at these utils as well.

---

