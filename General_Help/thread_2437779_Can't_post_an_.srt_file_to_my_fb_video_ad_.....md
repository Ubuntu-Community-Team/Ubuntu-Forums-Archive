---
title: "Can't post an .srt file to my fb video ad ...."
date: 2020-02-29
forum: General Help
---

### Post by dbee on 2020-02-29
I'm on ubuntu 19.10 and facebook won't accept my .srt file to accompany my video in ads manager.

I'm downloading the facebook specific .srt file from rev.com. But ubuntu changes the filename from 'my.file' to 'my_file'.

Are multiple '.' allowed in linux files ? Even when i change the filename and upload it. All i get is this error from FB
```

(#100) Invalid file. Expected file of one of the following types: application/octet-stream, text/plain

```
I've tried changing the file extension to .txt but no joy.

The only thing left to do is to boot up windows and use that instead for .srt file uploads to facebook :-(

Filename : haha Google Analytics ad 29 Feb 2020 13.08.43.en_US .srt
Movie Name: haha Google Analytics ad 29 Feb 2020 13.08.43.mp4

Is this an ubuntu issue or a FB issue ?

Thanks

---

### Post by TheFu on 2020-02-29
I don't use FB, but why not mux the SRT into the video file and upload that?  Is that a dumb question?

```

mkvmerge -o "haha Google Analytics ad 29 Feb 2020 13.08.43.mkv" \
                           "haha Google Analytics ad 29 Feb 2020 13.08.43.mp4" \
                           "haha Google Analytics ad 29 Feb 2020 13.08.43.en_US .srt"
```

Any files with odd characters, must be quoted.
If you stop using spaces in filenames, life will be easier.  GUI programs shouldn't have any issues with funny filenames, but when people create scripts that get used by some programs, it is common for whitespace to be used as a delimiter for different inputs.

Different file systems have limitations, not the OS.  If a native Linux file system is being used, like ext2, 3, 4, then pretty much any characters are supported provided the total length is under 4KB.  Filenames that aren't allowed in Windows are perfectly valid under Linux, unless a Windows file system like NTFS, FAT32 or exFAT is being used. Then the limit for those file systems are the issue, not Linux.

If you like, you can create a file named "............" on Linux.   Or ". . . . . . . .     ......       ...........    .      . ..end.srt"

---

### Post by dbee on 2020-02-29
For some reason the captions don't come out on FB with the mkvmerge. 

It comes out fine on my desktop. I really don't know what to think. Is it possible FB can strip the captions ?

---

### Post by dbee on 2020-02-29
Yeah, it works when i dual boot to windows. Must be an ubuntu thing. 

Anyone have any ideas ? I can redo the video and leave out the spaces i suppose...

---

### Post by TheFu on 2020-02-29
> **dbee said:**
> Yeah, it works when i dual boot to windows. Must be an ubuntu thing. 

Anyone have any ideas ? I can redo the video and leave out the spaces i suppose...

Why redo anything, just rename the file.

It could be a facebook *doesn't like the browser* thing.  Have you tried a different browser?  Perhaps lynx or dillo?

A few websites are hostile to anyone running non-MSFT or non-Apple programs. Sometimes, just changing the user-agent the browser sends to the webserver solves it.

---

### Post by Holger_Gehrke on 2020-02-29
I think it might have something to do with the fact that Ubuntu has a more complete database of mime-types. I just tried to upload an srt file into my files here on the forum using Firefox  and checked the headers and the content that was sent with the web-developer-tools. It sent a mime type of 'application/x-subrip'. While that is the correct type, FB says it expects 'application/octet-stream' (a basic type that means 'I don't really know what this is') or 'text/plain' (of which 'application/x-subrip' is a sub-type).

Holger

---

### Post by dbee on 2020-03-01
Thanks Holger_Gehrke,

That sounds like it might be a good bet for fixing the issue. 

One question, how do i alter the mime type of a file upload using the web developer extension (for chrome if possible) ... ?

I can't find anything on google ...

Cheers,

dbee

---

### Post by Holger_Gehrke on 2020-03-01
Can't help you with chrome since I don't use it and the web-developer tools in Firefox don't offer an option to override mime-types. In Firefox there's two options to try and fix this problem. One of them is Firefox-specific (changing the mimeTypes.rdf file in your profile-directory) and is not well enough documented for me to understand what to put in there. The other is to change the (system-wide) mime-database and comment out (or remove) the "application/x-subrip" type.

But before we try that: what happens if you change the extension to '.txt' ? Will FB accept a txt-file as srt-subtitles ? Since the distinction between 'text/plain' and 'application/x-subrip' in the mime-database depends on the extension, renaming the file to have a .txt extension should make the browser upload the file as plain text. If Facebook accepts that, it would be the easiest way to fix the problem.

If that doesn't work, you need to edit the file '/usr/share/mime/packages/freedesktop.org.xml'. Since that's a system file, the right way to edit it is 'sudoedit /usr/share/mime/packages/freedesktop.org.xml' in a terminal (sudoedit will ask for your password and will not give you any feedback while entering it; just type it and hit enter). Search the file for 'subrip' (if sudoedit uses nano on your system -- the default, AFAIK -- then search is ctrl-w). You'll find a line that says '<mime-type type="application/x-subrip">'. If you want to leave the file-type in there but deactivate it, put '<!-- ' at the beginning of the line, go down until you find a line that says '</mime-type>' and put ' -->' at the end of that line. Normally that would be it, but a few lines above the </mime-type> is a line which has a " --> " in a match-rule. Since that would confuse the parser, you need to change that line, too. I put 'REMOVE_THIS_WHEN_UNCOMENTING' between the two dashes in the " --> ". Alternatively you could just delete everything from the '<mimetype type="application/x-subrip">' to the '</mimetype>'. Save and exit the editor (in nano: ctrl-o and ctrl-x). Now you need to make the system update and reread the mime-database with 'sudo update-mime-database /usr/share/mime'. If this doesn't give any errors, then you're done. If you were to run 'mimetype path/to/some/file.srt' (replace the obvious ...) you'll get 'text/plain'.

One problem with this approach: if the package 'shared-mime-info' is updated it will probably wipe out your changes.

Holger

---

### Post by dbee on 2020-03-02
I've edited /etc/mime.types and changed the .srt setting to application/octet-stream or whatever but it still doesn't work.

Do I have to restart the system or something ?

Tried above method to edit the mime type. But had to close terminal permaturely. Now ubuntu is all messed up. Bummer.

---

### Post by shera77 on 2020-09-01
Was dealing with the same issue and found a solution for me (for chromium based browser, tested with Vivaldi):

Install the extension "Modify Content-type": [https://chrome.google.com/webstore/detail/modify-content-type/jnfofbopfpaoeojgieggflbpcblhfhka](https://chrome.google.com/webstore/detail/modify-content-type/jnfofbopfpaoeojgieggflbpcblhfhka)

Then create a new rule:
[IMG]https://www.hostpic.org/images/2009011743540080.png[/IMG]


[TABLE="width: 1814"]
[TR]
[TD]URL Filter:[/TD]
[TD].* (I left it as wide as possible, but can also be more narrow)[/TD]
[/TR]
[TR]
[TD]Original Type:[/TD]
[TD]application/x-subrip[/TD]
[/TR]
[TR]
[TD]Replacement Type:[/TD]
[TD]application/octet-stream[/TD]
[/TR]
[TR]
[TD]Disposition:[/TD]
[TD]<unchanged>
[/TD]
[/TR]
[/TABLE]

With this rule in place I can upload SRT files to FB Ad Manager.

---

