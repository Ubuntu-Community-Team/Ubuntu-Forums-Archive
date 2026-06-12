---
title: "Google Drive and text files: issue with line endings?"
date: 2014-08-23
forum: General Help
---

### Post by vasa1 on 2014-08-23
I want to upload text files to my Google Drive and have encountered some difficulty.

For example, I run **man grep** in lxterminal and copy some of the output using Shift+Control+C.

I then paste the text into nano using Shift+Control+V, and into Geany, Leafpad, Juffed and LibreOffice Writer using Ctrl+V and save these files making sure to use the "save as text" option for LibreOffice Writer.

I then upload all of these files to Google Drive allowing for conversion to Google Docs format. However, only the LibreOffice Writer file is directly viewable. If I try open any of the other files, I'm told they can't be viewed but only downloaded; some third party apps are suggested but that doesn't interest me.

When I run **file** on these text files, I see this:
```

    $ file *.txt
    geany.txt:   ASCII text
    juffed.txt:  ASCII text
    leafpad.txt: ASCII text
    libre.txt:   UTF-8 Unicode (with BOM) text, with CRLF line terminators
    nano.txt:    ASCII text
    $ 
```

Why does **file** see these text files the way it does?

Also, **ls -l** shows me that the file created by LibreOffice Writer is 1313 bytes whereas the others are smaller, all with a size of 891 bytes.

Can I set my other text editors, at least Geany, Leafpad and nano, to give me the same type of file I get with LibreOffice Writer?

In Leafpad, I tried Character Coding: Current Locale (UTF-8) and CR+LF but that file is still useless in Google Drive and **file** shows "ASCII text, with CRLF line terminators"

---

### Post by steeldriver on 2014-08-23
At least with Geany, it appears to be possible to add the BOM ('Document' --> 'Write Unicode BOM')

```

$ file mangrep-geany-bom.txt 
mangrep-geany-bom.txt: UTF-8 Unicode (with BOM) English text

```

Don't know if that helps (I don't use google docs)

---

### Post by tgalati4 on 2014-08-23
I have noticed that Google Drive behaves slightly differently between using on Firefox and using on Chrome.  It's possible that Drive does not know how to handle pure text files--since most people would be collaborating in a Word document, not a simple text file.  For text files, I use Evernote for the cloud and *zim* locally.

I bet if you save your text files as RTF then they would get stored and displayed properly.  Not useful for scripts, but OK if they are just random text notes.

---

### Post by vasa1 on 2014-08-23
@steeldriver, @tgalati4: thanks! I found the Document > BOM option in Geany. That didn't seem to help Google Docs open the file.

I vaguely remember being able to do stuff before but I can't now. Tried with both Firefox and Google Chrome. Anyway, Google Drive can at least serve as my third backup if nothing else.

---

### Post by tgalati4 on 2014-08-23
That is a general issue with cloud services.  They change without notice or they simply drift away.  There are several options for storing files in the cloud and you can set up your own server as a backup and file server.

What is the specific Use Case that you are trying to solve?  Do you need to open these text files from multiple locations?  Are they simply text notes that you want to have handy?  Are they scripts that you need to migrate to several machines?

---

### Post by mcduck on 2014-08-23
Drive definitely does handle .txt files, I just tested with both pure ASCII and UTF-8 encoded files and all stored correctly, display previews of the contents, and can be opened with Google Docs (atlhough opening the files for editing will convert them into Google's own format, so if you want to keep it as a normal text file perhaps use the Open With->Drive Notepad option or some other third-party app.

(I'm using Firefox, so if there's any difference between FF and Chrome then that could still be a reason. Although it sounds kind of strange if they didn't support this on their own browser)

---

### Post by vasa1 on 2014-08-23
> **tgalati4 said:**
> ...
What is the specific Use Case that you are trying to solve?  Do you need to open these text files from multiple locations?  Are they simply text notes that you want to have handy? ...

Well, the first point is that I rightly or wrongly seem to remember being able to store plain text files (after switching to Linux) on Google Drive and being able to view them by just double-clicking on them in Google Drive.

The files are just some things, plain text, small html files, small spreadsheets, that I may want to share with others who could access the link using mobile devices of any OS.

If I'm using Google Drive, I don't mind playing by their rules ... as soon as I know what those are.

Plus my finding **on my system** that not all text files are equal piqued my interest. And seeing something like [http://blog.codinghorror.com/content/images/uploads/2010/01/6a0120a85dcdae970b0120a86e2a1c970b-pi.gif](http://blog.codinghorror.com/content/images/uploads/2010/01/6a0120a85dcdae970b0120a86e2a1c970b-pi.gif) got me more worked up.

> **mcduck said:**
> Drive definitely does handle .txt files, I just tested with both pure ASCII and UTF-8 encoded files and all stored correctly, **display previews of the contents, and can be opened with Google Docs** (atlhough opening the files for editing will convert them into Google's own format, so if you want to keep it as a normal text file perhaps use the Open With->Drive Notepad option or some other third-party app.

(I'm using Firefox, so if there's any difference between FF and Chrome then that could still be a reason. Although it sounds kind of strange if they didn't support this on their own browser)
@mcduck, the part in bold exactly what I don't see, hence the thread :(

Just to recap, no issue with the storage, it's just that viewing/opening these files now seems to require a 3rd part app.

---

### Post by mcduck on 2014-08-24
well, it really shouldn't require a third-party app, since both previews and viewing the .txt files works just fine for me. (This includes .txt files with different character encodings and different line ending styles).

I only need the third-party app if I want to *edit* the .txt file without converting it into Google Docs format.

Someone suggested Drive might work differently based on your browser. Which one are you using?

Edit: Also, I have the option to convert uploaded files *disabled*. Otherwise I'd end witha  google document, not a pure text file.

---

### Post by vasa1 on 2014-08-24
> **mcduck said:**
> well, it really shouldn't require a third-party app, since both previews and viewing the .txt files works just fine for me. (This includes .txt files with different character encodings and different line ending styles).

I only need the third-party app if I want to *edit* the .txt file without converting it into Google Docs format.

Someone suggested Drive might work differently based on your browser. Which one are you using?

Edit: Also, I have the option to convert uploaded files *disabled*. Otherwise I'd end witha  google document, not a pure text file.
I use both Firefox and Chrome for separate gmail accounts. Both are the latest stable versions of the browser.

I've tried with both convert and "don't convert" options. 

For now, it's only the text files saved by LibreOffice Writer that work.

---

### Post by vasa1 on 2014-08-24
Oops! It looks like I need to provide a suffix. Then, all is well. So after uploading nanorc (no conversion), there's no preview but if I rename the file to nanorc.txt (or even nanorc.html or nanorc.css) and upload (no conversion), it previews just fine.

---

### Post by mcduck on 2014-08-24
yeah, Drive detects files based on suffix, which is slightly annoying sometimes, for example I use markdown quite commonly, and being able to name the files as .md would make it a lot easier for other programs to use them correctly, but Drive will only preview them if they are saved with .txt suffix...

If it helps anything, Drive does support double suffix, so *somefile.md.txt* works fine, and then you'll just have to remember to remove the extra suffix when using the file outside of Drive.

---

### Post by vasa1 on 2014-08-24
> **mcduck said:**
> yeah, Drive detects files based on suffix, which is slightly annoying sometimes, for example I use markdown quite commonly, and being able to name the files as .md would make it a lot easier for other programs to use them correctly, but Drive will only preview them if they are saved with .txt suffix...

If it helps anything, Drive does support double suffix, so *somefile.md.txt* works fine, and then you'll just have to remember to remove the extra suffix when using the file outside of Drive.
Thank you for confirming the need for using a suffix. That's a relief :)

---

### Post by vasa1 on 2014-08-24
Although I've marked this thread [SOLVED], I later remembered that in my first post, I *had* used suffixes. So why things worked later but not initially is beyond me.

---

### Post by tgalati4 on 2014-08-24
Also understand that the Google Drive client relies on a properly-loaded web page.  If there are any errors in the web page code, interacting with your document can become cumbersome and scary.  Sometimes closing out the tab and reloading fixes things.  Not confidence building.

---

