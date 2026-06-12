---
title: "What is a looped directory?"
date: 2022-08-29
forum: General Help
---

### Post by John Jason Jordan on 2022-08-29
I have a workhorse font that I need for work in linguistics. I have used it for years without a problem. Today I did the dist-upgrade from Xubuntu 20.04 to 22.04.1, and after it finished I decided to tidy up my fonts - to get rid of fonts installed by applications and otherwise that I don't need. After deleting a lot of them, some via Synaptic and others by nuking files in /usr/share/fonts I ran 'fc-cache -fv,' which gave me:

```
/home/jjj/.local/share/fonts/Unknown Vendor: skipping, looped directory detected 
``` 

I have long kept my font in ~/.fonts, and sure enough, LO Writer can no longer see it. I tried Font Manager, where it appears with a line through it. 

I have never heard of a looped directory, nut I have a small clue. At the top of the ~/.fonts folder there is a small file '.uuid,' and it opens in a text editor, displaying what looks like a uuid code. More importantly, I cannot delete it; that is, if I delete the file it instantly reappears. And when it reappears the uuid code is different.

Furthermore, there is also a .uuid file in /usr/share/fonts, and another one in each of its subfolders. And deleting any of them produces a new one in a few seconds, always with a new uuid code.

WTH?

---

### Post by &amp;KyT$0P# on 2022-08-30
Please post the output from running this command in Terminal -
```
ls -la /home/jjj/.local/share/fonts
```

---

### Post by John Jason Jordan on 2022-08-30
> **halogen2 said:**
> Please post the output from running this command in Terminal -
```
ls -la /home/jjj/.local/share/fonts
```

I keep my personal fonts (i.e., fonts purchased elsewhere) in ~/.fonts, not in ~/.local/share/fonts.

```
ls -la /home/jjj/.local/share/fonts
total 12
drwxr-xr-x  2 jjj jjj 4096 Aug 29 23:33 .
drwxrwx--- 81 jjj jjj 4096 Aug 30 00:02 ..
-rw-r--r--  1 jjj jjj   36 Aug 29 19:27 .uuid
```

```
ls -la /home/jjj/.fonts
total 121616
drwxrwxr-x   2 jjj jjj    36864 Aug 29 23:27 .
drwxr-xr-x 194 jjj jjj    20480 Aug 29 23:22 ..
-rwxrwxr-x   1 jjj jjj   169448 Aug  7  2013 ACaslonPro-BoldItalic.otf
-rwxrwxr-x   1 jjj jjj   142728 Aug  7  2013 ACaslonPro-Bold.otf
-rwxrwxr-x   1 jjj jjj   167268 Aug  7  2013 ACaslonPro-Italic.otf
-rwxrwxr-x   1 jjj jjj   161568 Aug  7  2013 ACaslonPro-Regular.otf
-rwxrwxr-x   1 jjj jjj   170168 Aug  7  2013 ACaslonPro-SemiboldItalic.otf
-rwxrwxr-x   1 jjj jjj   165700 Aug  7  2013 ACaslonPro-Semibold.otf
-rwxrwxr-x   1 jjj jjj    89580 Aug  7  2013 AGaramondPro-Italic.otf
-rwxrwxr-x   1 jjj jjj   118940 Aug  7  2013 AGaramondPro-Regular.otf
-rwxrwxr-x   1 jjj jjj    77464 Aug  7  2013 AGaramondPro-SemiboldItalic.otf
-rwxrwxr-x   1 jjj jjj    95648 Aug  7  2013 AGaramondPro-Semibold.otf
-rwxrwxr-x   1 jjj jjj   128184 Aug  7  2013 AJensonPro-BoldCapt.otf
-rwxrwxr-x   1 jjj jjj   124696 Aug  7  2013 AJensonPro-BoldDisp.otf
-rwxrwxr-x   1 jjj jjj   159940 Aug  7  2013 AJensonPro-BoldItCapt.otf
(plus many more)
```

1) I don't know why the first command said there were 12 files in ~/.local/share/fonts, because all that was in there was the .uuid file.
2) As for ~/.fonts, I have always kept fonts purchased or downloaded from elsewhere, rather that from the repositories, in ~/.fonts, because it is simpler than navigating to ~/.local/share fonts. This has worked perfectly for me since I first installed Ubuntu Breezy Badger in 2005.
3) Just now I noticed that the ls command for ~/.local/share/fonts displayed the .uuid file, but the ls command for ~/.fonts did not. Yet in Thunar or other GUI file managers there is a .uuid file in each directory.

I should have mentioned at the beginning that there is a 1TB Samsung M.2 drive with a 100GB partition for / and the remainder of the drive in a partition for /home. Hence the fonts in /usr/share/fonts is on / and the other two folders are on /home. I don't know why that should matter; it never has before.

This problem appeared only after the fist-upgrade to 22.04.1. Maybe something happened with the upgrade.

---

### Post by &amp;KyT$0P# on 2022-08-30
Maybe try deleting the entire contents of [FONT=Courier New]~/.cache/fontconfig[/FONT] and then run [FONT=Courier New]fc-cache -f -v[/FONT] again?

It is normal that a .uuid file exists in each font directory.

---

### Post by John Jason Jordan on 2022-08-30
> **halogen2 said:**
> Maybe try deleting the entire contents of [FONT=Courier New]~/.cache/fontconfig[/FONT] and then run [FONT=Courier New]fc-cache -f -v[/FONT] again?

It is normal that a .uuid file exists in each font directory.

Great suggestion! Sadly, it made no difference. :(  Actually, I just renamed ~/.cache/fontconfig by appending .old, then re-ran the command. Same looped directory error messages, but it produced a new fontconfig cache, so at least the command is doing *something*. I opened the new fontconfig (it's a directory) and found a zillion files that looked like:

[INDENT][/INDENT]01ddb72a-c26c-4250-8dc9-bed089222573-le64

Each file has a different number. I have no idea what they're pointing to.

Then, for a new experiment, I copied all the fonts in ~/.fonts to ~/.local/share/fonts, renamed the original ~/.fonts folder and created a new empty one, then ran the command again. It still gave me the looped directory error messages. But this time I read the results more carefully and found these lines at the end:

```
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/jjj/.cache/fontconfig: cleaning cache directory
/home/jjj/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded
```

Not sure what those lines mean.

---

### Post by &amp;KyT$0P# on 2022-08-30
> **John Jason Jordan said:**
> Same looped directory error messages, 

Looks like "skipping, looped directory" just means that [FONT=Courier New]fc-cache[/FONT] already processed that directory.  I tested on my system, and for each "looped directory" message, there was a prior line in the entire verbose output where that directory was processed (successfully in my case).  If you also have other line(s) in the full fc-cache output that reference [FONT=Courier New]/home/jjj/.local/share/fonts/Unknown Vendor[/FONT], maybe the prior line(s) will be more informative?

What I don't understand is why [FONT=Courier New]fc-cache[/FONT] is trying at all to process a non-existant directory, even when the existing fontconfig cache has been totally deleted.

> this time I read the results more carefully and found these lines at the end:

```
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/jjj/.cache/fontconfig: cleaning cache directory
/home/jjj/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded
```

Not sure what those lines mean.

The first one means you don't have write permission to [FONT=Courier New]/var/cache/fontconfig[/FONT] (because you're not running [FONT=Courier New]fc-cache[/FONT] as root).

Not sure what the second line means exactly.

The third line just means that [FONT=Courier New]/home/jjj/.fontconfig[/FONT] does not exist on your system, which is normal for 20.04 and later.

The fourth line seems self-explanatory.

---

