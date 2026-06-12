---
title: "I need a text editor that saves files as .TXT (e.g: Windows readable)"
date: 2007-05-29
forum: General Help
---

### Post by enthusaroo on 2007-05-29
Hey everyone,

I've been using Ubuntu for the last two months. During that time I was using Gedit for saving all of my text. I was using it because I thought it was basically the same as Notepad.exe for Windows, except with more features.

However, I just found out recently that all of the files that I saved using Gedit under Ubuntu is not readable. Plus, the formatting is completely off when I try to open it under Windows. I even copy and pasted a Gedit saved text file to Google Docs and Spreadsheets, but the formatting is still screwed up when I try to save it as a .TXT file, download it, and open it.

So, can somebody please suggest one of the two following things, either:
A) A simple text editor for Ubuntu that saves files in .TXT format, so it can be readable by Windows.
or
B) A text editor for Windows that is able to read whatever format the Gedit program uses.

I'm disappointed, because now I have hundreds of text files that I saved in Ubuntu over the last two moonths that I am unable to use on other (Windows) computers. :( :( :( :(

---

### Post by eentonig on 2007-05-29
Just change the extension for the files to .txt

Windows will be able to open them.

Concerning your formatting. What exactly is the problem? <returns> not used as you are used to?


Btw. Install Notepad++ A way better notepad

---

### Post by mozetti on 2007-05-29
I think you can use one of the command-line text editors, like nano, to do this. To be honest, I thought you could do this with gEdit, too. But, I can't say I've tried it either -- I just assumed it would work. Do you think it could be a problem with the encoding you're using (UTF-8 vs ISO)?

---

### Post by enthusaroo on 2007-05-29
> **eentonig said:**
> Just change the extension for the files to .txt

Windows will be able to open them.

Concerning your formatting. What exactly is the problem? <returns> not used as you are used to?


Btw. Install Notepad++ A way better notepad

Hi eentonig,

>>Just change the extension for the files to .txt

I tried that. I mean Windows can open the file in Notepad, but again the formatting is completely off.

>>Concerning your formatting. What exactly is the problem? <returns> not used as you are used to?

Like for example, when I open it under Windows it does format the sentences or paragraphs correctly at all. It just all runs together as one big paragraph with no breaks at all. :(

---

### Post by enthusaroo on 2007-05-29
> **mozetti said:**
> I think you can use one of the command-line text editors, like nano, to do this. To be honest, I thought you could do this with gEdit, too. But, I can't say I've tried it either -- I just assumed it would work. Do you think it could be a problem with the encoding you're using (UTF-8 vs ISO)?

I'm still new to Linux, so I think I'd prefer to have at least a basic graphical text editor. I'm not really good with command line... at all (yet). :p

I mean, gEdit is a fine program. I think it's perfect for what I need. The ONLY problem is the formatting. I just have to save the text files that I save in gEdit as .TXT format. I just assumed when I started using gEdit that it was saving files in .TXT format, but just discovered a few days ago that it saves it as some unknown format.

---

### Post by AZzKikR on 2007-05-29
My guess is that when GEdit saves your file, it will save the linebreaks as one character. 
OK, more clarification. When Windows Notepad saves the following text file:
```
Hi, this is a test.
With some text.
```
What actually is written to a file is something like this:
```
Hi, this is a test.\r\nWith some text.
```

The \r and \n are non-printable characters, equivalent to Carriage Return (hex code 0x0A) and Line Feed (hex code 0x0D). The text editor knows how to interpret these characters, and notepad will thus display a normal linebreak like this.

Linux/Unix based systems usually writes the following when saved in GEdit:
```
Hi, this is a text.\nWith some text.
```
Not that the \r (carriage return) is not written. 

If you open your file wite Wordpad (write.exe), I think the formatting will be viewed correctly. Notepad does not intepret the single line-feed as a normal line break if I am not mistaken.

If not, you'll have to save the text in GEdit using different line-breaks (if that is possible, I am not on my Ubuntu box at the moment), or you'll have to convert the single \n characters to \r\n using a simple script. I once wrote a Perl script (one line script) which converts every \n with \r\n, and \r\n to \n (which means: from Unix to Windows, and Windows to Unix).

Does this clarify things a bit more? If not, just ask. I wrote this in under 2 minutes or something :)

---

### Post by aysiu on 2007-05-29
Use Notepad++

---

### Post by public_void on 2007-05-29
Open with Wordpad. Or find out what encoding notepad uses, then save in that format. From the save as dialogue box set the "Character Coding" to "Add or Remove". Then remove the default your currently using and replace with the standard notepad uses.

---

### Post by reclusivemonkey on 2007-05-29
You might also want to install the package "tofrodos". You can then use 

```

unix2dos

```

and

```

dos2unix

```

to convert files from one to another. Just to clarify, gEdit DOES save as text, its just that Unix and Dos handle line feeds differently.

---

### Post by tom72 on 2007-05-29
Or use Programmers Notepad under Windows, it's not only a great replacement for notepad.exe but also converts your files to the windows linebreaks
It's open source of course

[www.pnotepad.org](www.pnotepad.org)

---

### Post by enthusaroo on 2007-05-29
> **AZzKikR said:**
> My guess is that when GEdit saves your file, it will save the linebreaks as one character. 
OK, more clarification. When Windows Notepad saves the following text file:
```
Hi, this is a test.
With some text.
```
What actually is written to a file is something like this:
```
Hi, this is a test.\r\nWith some text.
```

If you open your file wite Wordpad (write.exe), I think the formatting will be viewed correctly. Notepad does not intepret the single line-feed as a normal line break if I am not mistaken.

Actually, you're spot on! If I open the file with Wordpad, then it does format the text correctly! Thank you.

Only issue now is figuring out how to get the gEdit generated text files to open automatically with Wordpad whenever I double click on them. Any ideas?

As far as I can tell, the gEdit files seem to have no extention(?), so there doesn't seem to be any way to make it so these files automatically "open with" Wordpad.

---

### Post by aysiu on 2007-05-29
> **enthusaroo said:**
> 
Only issue now is figuring out how to get the gEdit generated text files to open automatically with Wordpad whenever I double click on them. Any ideas?

As far as I can tell, the gEdit files seem to have no extention(?), so there doesn't seem to be any way to make it so these files automatically "open with" Wordpad. You'll have to add the .txt extension manually in Gedit.

But Gedit has nothing to do with files automatically opening with Wordpad in Windows. That's entirely decided by Windows. In Windows, right-click on the .txt file, select *open with* > *choose program...* and then select *Wordpad* and make sure the box next to *Always use selected program to open this kind of file* is checked (or ticked).

---

### Post by LaRoza on 2007-05-29
For the best text/code editor, try Crimson Editor. Although almost any notepad replacement, like Notepad++, Notepad2, and NotepadSX are better than MS Notepad.

For file extension, just type them in when you save, Windows programs usually save as a default and append the file extension, but you can type them yourself.

Windows doesn't do any thinking when it sees a file, all it sees are the file extensions and uses that to determine what program opens it.

---

### Post by enthusaroo on 2007-05-29
> **aysiu said:**
> You'll have to add the .txt extension manually in Gedit.

But Gedit has nothing to do with files automatically opening with Wordpad in Windows. That's entirely decided by Windows. In Windows, right-click on the .txt file, select *open with* > *choose program...* and then select *Wordpad* and make sure the box next to *Always use selected program to open this kind of file* is checked (or ticked).

Right, I know that gEdit has nothing to do with the files opening under Windows. What meant was, I wish someone on these forums knew how to set it up so that it can open automatically with Wordpad.

For this particular file type there isn't any "open with" option when I right click.

---

### Post by aysiu on 2007-05-29
> **enthusaroo said:**
> Right, I know that gEdit has nothing to do with the files opening under Windows. What meant was, I wish someone on these forums knew how to set it up so that it can open automatically with Wordpad.

For this particular file type there isn't any "open with" option when I right click.
You have a .txt extension and there's *no* open with option in the context menu? That's weird. Well, in that case, double-clicking the file may just force Windows to give you the *open with* option anyway.

---

### Post by tszanon on 2007-05-29
Since gEdit lets you use any extension you want, you can save every file in gEdit as .doc
They'll open automatically with Wordpad.

OR

You can open Windows Explorer, then (please take care: Windows XP here, in portuguese. Names may be different):
Click Tools menu > Folder Options > File Types tab

There'll be hundreds of file types in the box there, including TXT. Choose it, then press Advanced.
I suggest you to create a new entry, telling it to open it using wordpad, and setting it as the default action:
Click New > Enter a descriptive action name ("Open with Wordpad") > set the command line > ok
Select the new item > click Default

The command line looks like this, if I recall correctly:
"C:\Arquivos de programas\Windows NT\Acessórios\wordpad.exe" %1
It's just the full path to wordpad.exe and the %1.

> **aysiu said:**
> Well, in that case, double-clicking the file may just force Windows to give you the *open with* option anyway.
That would happen only if the file has no extension. If the file has a known extension (TXT), windows executes the default action when double-clicked.

---

### Post by stchman on 2007-05-29
> **enthusaroo said:**
> Hey everyone,

I've been using Ubuntu for the last two months. During that time I was using Gedit for saving all of my text. I was using it because I thought it was basically the same as Notepad.exe for Windows, except with more features.

However, I just found out recently that all of the files that I saved using Gedit under Ubuntu is not readable. Plus, the formatting is completely off when I try to open it under Windows. I even copy and pasted a Gedit saved text file to Google Docs and Spreadsheets, but the formatting is still screwed up when I try to save it as a .TXT file, download it, and open it.

So, can somebody please suggest one of the two following things, either:
A) A simple text editor for Ubuntu that saves files in .TXT format, so it can be readable by Windows.
or
B) A text editor for Windows that is able to read whatever format the Gedit program uses.

I'm disappointed, because now I have hundreds of text files that I saved in Ubuntu over the last two months that I am unable to use on other (Windows) computers. :( :( :( :(

I have had no problem with Gedit and then opening the resulting text files in notepad.  Notepad kind of blows so I recommend using Notepad++ for Windows.

[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

Notepad++ absolutely rocks.  It also puts a line in your right clicks in explorer "Open with Notepad++".  Thank the open source community.

---

### Post by enthusaroo on 2007-05-30
> **aysiu said:**
> You have a .txt extension and there's *no* open with option in the context menu? That's weird. Well, in that case, double-clicking the file may just force Windows to give you the *open with* option anyway.

What I meant by "this particular file type" is the the format generated by gEdit. The gEdit files do not have an "open with" option under Windows.

---

### Post by dfox8895 on 2007-05-30
open tha txt file in wordpad first.  This will preserve the formatting.  Then save it as txt.

---

### Post by aysiu on 2007-05-30
> **enthusaroo said:**
> What I meant by "this particular file type" is the the format generated by gEdit. The gEdit files do not have an "open with" option under Windows.
And what I mean is that if you save the Gedit file with a .txt extension, there should be an **Open with** option in the context menu in Windows; and if you save the Gedit file with no extension, you can double-click the file in Windows, and the **Open with** dialogue box will appear after a minute or so.

---

### Post by mozetti on 2007-05-30
> **enthusaroo said:**
> For this particular file type there isn't any "open with" option when I right click.

As aysiu said, you'll need to add the .txt extension yourself. To set up Windows to always use WordPad for .txt files, you need to use the "Open with" menu as aysiu also explained.

If you don't see the "open with..." option, then hold down the "Shift" key when you right click the file. That should give you all the commands in the context menu.

As an aside -- file extensions aren't as important in Linux as they are in Windows. From my experience, in Linux they are just additional description about the file. For example, .config for configuration files, .bak or .old for backups of config files, .txt for text files, etc.

---

### Post by aysiu on 2007-05-30
No matter what you do in Gedit, once the file goes to Windows--depending on whether you have the .txt extension or not--you're going to get one of these four options (see attached images). Regardless of which option you get, there is *always* a way to associate that file with being opened by default with Wordpad.

I would still recommend Notepad++, however. Wordpad kind of stinks.

---

