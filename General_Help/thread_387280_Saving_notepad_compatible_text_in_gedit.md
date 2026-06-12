---
title: "Saving notepad compatible text in gedit"
date: 2007-03-18
forum: General Help
---

### Post by steve196 on 2007-03-18
How do i make gedit save text in a way, that is read correctly by microsoft notepad?
Thanks!

---

### Post by maxamillion on 2007-03-18
Install this on your windows machine: [http://www.heelana.com/Programs/Unix2Win/unix2win.html](http://www.heelana.com/Programs/Unix2Win/unix2win.html)

---

### Post by yopnono on 2007-03-18
> **steve196 said:**
> How do i make gedit save text in a way, that is read correctly by microsoft notepad?
Thanks!

You can also use wordpad.

---

### Post by steve196 on 2007-03-18
Thanks for the answers.
I know there are windows programs, that can read and write unix text. But i need it the other way round.

---

### Post by fragos on 2007-03-18
The primary difference between Microsoft, Unix and MAC text files is the end of line.  MS = CRLF, Unix = CR and MAC = LF.  I couldn't find a parameter in gedit for this but have seen it in other text editors like kate.  There may very well be a plugin for gedit that will do what you want or you might write one yourself with sed.   Check out gedit Tools-> External Tools and it will show you the sed line that removes trailing spaces..

---

### Post by steve196 on 2007-03-19
Thank you!
"kate" does it.

---

### Post by epictete on 2007-10-07
If you prefer a **gtk program** to Kate (QT program), **Mousepad** does it in the window "Record under..." where you can choose between LF (Linux) or CRLF (Windows).

This is a **very real problem** for, with the tools of Gnome, you can't give a text file to colleagues or friends that are using Windows.

It's really a pity that after all those years it is always impossible to do that simple thing  with the editor of Gnome. I like Gnome very much but I often feel like Linus about it's developpers !

---

### Post by epictete on 2007-10-08
******************
* CRLF - Notepad *
******************

[http://www.wischik.com/lu/programmer/crlf.html](http://www.wischik.com/lu/programmer/crlf.html)

**(c) 2002 Lucian Wischik**. These programs are free, and anyone can do with them whatever they like (except sell them or claim ownership).

Unix-format text files do not load properly into Notepad: their linebreaks are wrong. The problem is that unix expects linebreaks in the 'LF' format (\n), while Windows expects them in the 'CRLF' format (\r\n). The programs on this page provide two possible ways to convert LF into CRLF. You can use either program its own, or both together. They require Windows XP.

**crlf-notepad.exe** (72k)

[http://www.wischik.com/lu/programmer/crlf-notepad.exe](http://www.wischik.com/lu/programmer/crlf-notepad.exe)

This program acts as a wrapper around Notepad to convert LF into CRLF. To install it, first rename notepad.exe -> notepad-orig.exe and then rename crlf-notepad.exe -> notepad.exe. In this way, whenever any program thinks it is launching notepad, it will really be launching the CRLF wrapper first. Advantage: works no matter how notepad is invoked, be it from Internet Explorer's View Source menu or Send-To. Limitation: only works with notepad.

---

### Post by epictete on 2007-10-08
************
* Unix2Win *
************

[http://www.heelana.com/Programs/Unix2Win/unix2win.html](http://www.heelana.com/Programs/Unix2Win/unix2win.html)

**Unix2Win** is a tool that converts ASCII text files from Unix to Microsoft Windows format or vice versa.

Unix uses character code 10 (line feed) to separate text lines while Windows uses a combination of 13 (carriage return) and 10.

The free version lets you convert one file at a time. You can choose whether to save converted files to a common directory or to the original directory but adding a “_conv” suffix. F.e. data.txt becomes data_conv.txt.

If you need to convert large numbers of files you may be interested in the advanced version which allows you to convert multiple files in one step. Check the registration/download link below.

---

### Post by breaking on 2008-01-22
> **fragos said:**
>  There may very well be a plugin for gedit that will do what you want or you might write one yourself with sed.   Check out gedit Tools-> External Tools and it will show you the sed line that removes trailing spaces..

That was a great idea. I just made a script (inspired by a few google searches) that does it. Just enter the following as a script in the external tools plugin of gedit:

```
#!/bin/sed -f

s/\r//g
s/$//g
s/$/\r/
```

---

### Post by epictete on 2008-01-23
It works fine! Thank's very much **Breaking**!

To understand your script, it is important to know that:
"when searching, \r matches CR, but when replacing, \r inserts LF"
[http://vim.wikia.com/wiki/VimTip26](http://vim.wikia.com/wiki/VimTip26)

---

### Post by sandr- on 2008-01-23
I open notepad with wine ( default installed ), and copypaste my gedit/nano/... text inside. Then i save the txt somewhere and I can read it from windows !
Maybe a workaround to other solutions posted, but it works :)

---

### Post by epictete on 2008-01-23
That's an idea **Sandr-** but it necessits to have Wine installed and to know how to make it work.

Using Mousepad or the script for Gedit by **Breaking** seems simpler.

---

### Post by Rui Pais on 2008-01-23
scite allow to change line terminator too.

since it's much light then gedit, offering the same functionality and don't have extra dependencies it can be used to replace gedit as an all generic text editor (it can even work as IDE)

---

### Post by epictete on 2008-01-23
That's right **Rui Pais** !

PS. May be you know how to set in **Scite** the default encoding to utf-8 and the default EOL character  so that il's not different each time you open Scite and you save a file?

---

### Post by Rui Pais on 2008-01-23
> **epictete said:**
> That's right **Rui Pais** !

PS. May be you know how to set in **Scite** the default encoding to utf-8 and the default EOL character  so that il's not different each time you open Scite and you save a file?

That one exactly i don't know... check file of Global options (under Options menu)
There a lot to choose, and some not set by default options are commented...

just copy them to the user Options file (~/.SciTEUser.properties) uncommented.
Must be something like:
```
# Required for Unicode to work on GTK+:
LC_CTYPE=en_US.UTF-8
```
and
```
# Behaviour
#eol.mode=LF #<- change for your preference
#eol.auto=1

```

I personally always add the following too:
```
line.margin.visible=1
line.margin.width=5+
autocompleteword.automatic=1
toolbar.usestockicons=1
menubar.detachable=1
quit.on.close.last=1
```

HTH

---

### Post by heindsight on 2008-01-23
> **breaking said:**
> That was a great idea. I just made a script (inspired by a few google searches) that does it. Just enter the following as a script in the external tools plugin of gedit:

```
#!/bin/sed -f

s/\r//g
s/$//g
s/$/\r/
```

I understand the first and third substitutions, but what's the second one supposed to do? Surely that's a no-op? In the past, I've used this:
```
s/\([^\r]\)$/\1\r/g
``` to convert from Unix (or mixed formats, like what happens when you cat a Unix text file to a Dos text file) to DOS format.

> **epictete said:**
> It works fine! Thank's very much **Breaking**!

To understand your script, it is important to know that:
"when searching, \r matches CR, but when replacing, \r inserts LF"
[http://vim.wikia.com/wiki/VimTip26](http://vim.wikia.com/wiki/VimTip26)

AFAIK that's true for vim, but not for sed.
see [http://info2html.sourceforge.net/cgi-bin/info2html-demo/info2html?(sed.info.gz)Escapes](http://info2html.sourceforge.net/cgi-bin/info2html-demo/info2html?(sed.info.gz)Escapes)

---

### Post by epictete on 2008-01-23
**Rui Pais**, it works for the default EOL characters ; you can even make them be displayed by default with:

```
# Element styles
view.eol=1
```

It doesn't work for the default encoding that remains on 8bit but, after Googling, it seems that this setting isn't possible in the configuration file at this time !

**Thank's very much!**

---

### Post by epictete on 2008-01-23
> **heindsight said:**
> AFAIK that's true for vim, but not for sed.

So true **Heindsight**! Sorry but I'm a newbie!

> **heindsight said:**
> I understand the first and third substitutions, but what's the second one supposed to do? Surely that's a no-op? In the past, I've used this:
```
s/\([^\r]\)$/\1\r/g
``` to convert from Unix (or mixed formats, like what happens when you cat a Unix text file to a Dos text file) to DOS format.

Works perfectly!

Two newbie questions:
- [^\r]$ means "all but not CR" at the end of a line ; why must we use ( )
- why \1

**EDIT:** I have the answer to the 2 questions:
\1 Matches the same string that was matched by the first sub-expression in \( and \)
[http://vimdoc.sourceforge.net/htmldoc/pattern.html#/\r](http://vimdoc.sourceforge.net/htmldoc/pattern.html#/\r)
So we replace everything but a CR at the end of a line by the same thing plus a CR.
Sorry ; say I didn't ask it! :confused:

---

### Post by heindsight on 2008-01-23
> **epictete said:**
> 
Two newbie questions :confused: :
- [^\r]$ means "all but not CR" at the end of a line ; why must we use ( )
- why \1

Well, s/[^\r]$/\r/g would replace the entire string that matches [^\r]$ by \r, which means that for every line that ends in just an LF instead of CRLF, the last character of the line (before the LF) will be replaced by a CR. Putting \( \) around a part of the regular expression, groups the expression inside the parentheses so that it can be treated as a single unit, and referred back to later.

So, \([^\r]\)$ matches any character other than CR at the end of a line, and remembers whatever matched [^\r] so that it can be referred to again later using \1

EDIT:
haha, just saw your edit. Feels good to be able to find the answer yourself doesn't it ;)
btw. there are some differences between how sed and vim treat regular expressions and substitutions the site I linked to earlier is better if you want to learn sed. 
Or you could access the same information by using the command ```
info sed
``` in a terminal.

---

### Post by epictete on 2008-01-23
Thank's **Heindsight**: kind of you!

---

### Post by heindsight on 2008-01-23
hmmm, that sed script I posted earlier doesn't handle empty lines well.
this is better:
```
#!/bin/sed -nf
G
s/\([^\x0d]\|^\)\x0a/\1\x0d\x0a/g
P

```

---

### Post by stchman on 2008-01-23
> **steve196 said:**
> How do i make gedit save text in a way, that is read correctly by microsoft notepad?
Thanks!

Gedit does, the problem you are seeing is that Unix/Linux have a 1 byte carriage return while DOS has a 2 byte carriage return.

When you open the text file in Windows use Wordpad as it will correctly interpret the carriage return.

There is a package on Ubuntu called tofrodos that will do a unix2dos or dos2unix type conversion on text files.

```
sudo apt-get -y install tofrodos
```

You can use this page to learn it's usage.

[http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)

---

### Post by heindsight on 2008-01-23
> **stchman said:**
> 
There is a package on Ubuntu called tofrodos that will do a unix2dos or dos2unix type conversion on text files.


True, but writing your own sed scripts to do it is so much more fun. ;)

---

### Post by stchman on 2008-01-23
> **heindsight said:**
> True, but writing your own sed scripts to do it is so much more fun. ;)

You could also use a C program to fprintf out ASCII characters which would be even more loads of fun.

You could easily do a %c for 10 and 13.

---

### Post by epictete on 2008-01-23
> **heindsight said:**
> haha, just saw your edit. Feels good to be able to find the answer yourself doesn't it ;)

Yes Heindsight, and when you finaly find, you can say: yeah I've got it!
(but sometimes it's fine to have a teacher too! :wink:)

> btw. there are some differences between how sed and vim treat regular expressions and substitutions the site I linked to earlier is better if you want to learn sed.


Yes I've seen that and your page about sed is now in my bookmarks.

---

### Post by epictete on 2008-01-23
> **heindsight said:**
> hmmm, that sed script I posted earlier doesn't handle empty lines well.

As for your** new** script, the script by **Breaking** handles empty lines correctly as they don't remain as LF.

---

