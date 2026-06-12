---
title: "[SOLVED] wget forum thread pages?"
date: 2007-08-12
forum: General Help
---

### Post by Interestedinthepenguin on 2007-08-12
Is it possible to use wget to download all pages of a forum thread?  I've been trying, and am having poor luck.  

Here's the thread I'm trying to nab:  [http://forums.gentoo.org/viewtopic-t-117709.html?sid=85662bab2fd4dbaddbecd8d05ec46b5e](http://forums.gentoo.org/viewtopic-t-117709.html?sid=85662bab2fd4dbaddbecd8d05ec46b5e)

Thanks.

---

### Post by Interestedinthepenguin on 2008-02-05
No longer a wget noob, I tried it again:

```

wget -k -p http://forums.gentoo.org/viewtopic-t-117709-postdays-0-postorder-asc-start-{0,25,50,75,100,125,150,175,200,225,250,275,300,325,350,375,400,425,450,475,500,525,550,575,600,625,650,675,700,725,750}.html

```

Works perfectly.:razz:

PS:  Don't forget to use ```
--wait
```

---

### Post by Gadrin on 2008-02-12
> **Interestedinthepenguin said:**
> No longer a wget noob, I tried it again:

```

wget -k -p http://forums.gentoo.org/viewtopic-t-117709-postdays-0-postorder-asc-start-{0,25,50,75,100,125,150,175,200,225,250,275,300,325,350,375,400,425,450,475,500,525,550,575,600,625,650,675,700,725,750}.html

```

Works perfectly.:razz:

PS:  Don't forget to use ```
--wait
```


That's nice. Your wGet- fu is very impressive.

Can you get it to work on PHPBBS sites ? I had to write a special script so I could cut & paste a URL for a phpBBS / vBulletin BBS and have it go retrieve each of the pages. (Sorry I'm on Windows XP) 

Anyway I tried your sample but it only retrieves the first page of a multi-page phpBBS post.


For instance, here's a 3 page phpBBS topic that you should be able to see without being a member...

[http://www.phpbb.com/community/viewtopic.php?f=6&t=738475](http://www.phpbb.com/community/viewtopic.php?f=6&t=738475)

Can you get all three pages with wGet ? :confused:

---

### Post by Interestedinthepenguin on 2008-02-13
Thanks.  

 I'm no expert, but here ya go:  

```
wget -E -k -p -w3 http://www.phpbb.com/community/viewtopic.php?f=6\&t=738475\&st=0\&sk=t\&sd=a{,\&start={15,30}}
```

The first page doesn't link to the others (their links change):(, but the other pages link fine; they even link to the first page.  

Sometimes you have to study/play with the URL in order to get consecutive pages.

Note the backslashes in the command. If you don't use them when using certain characters (I know surely, &s and !s), wget (or bash?) will interpret them and download bad pages.

---

### Post by Gadrin on 2008-02-13
Are you getting good pages ?

I get two pages with "Requested Topic doesn't exist" on them.

It downloads the ROBOTS.TXT file and icons and some others, then:

FINISHED --22:09:34--
Downloaded: 103,243 bytes in 8 files
Converting [www.phpbb.com/community/viewtopic.php@f=6%5C.html](www.phpbb.com/community/viewtopic.php@f=6%5C.html)... 6-21
Converted 1 files in 0.012 seconds.
't' is not recognized as an internal or external command,
operable program or batch file.
'st' is not recognized as an internal or external command,
operable program or batch file.
'sk' is not recognized as an internal or external command,
operable program or batch file.
'sd' is not recognized as an internal or external command,
operable program or batch file.
The system cannot find the file {15,30}}.

And I cut & pasted your command line. 

Are you using a different/better version ?

C:\zCDROMS\wbtTemp>wget --help
**GNU Wget 1.10.2, a non-interactive network retriever.**
Usage: wget [OPTION]... [URL]...

---

### Post by Interestedinthepenguin on 2008-02-13
Yes, I'm getting good pages.  I also have the same version of wget and am working from a Windows PC.  

**EDIT: ** I just tried pasting my code into wget, and I, too, didn't come out with the desired results.  

Solution:```
wget -E -k -p -w3 http://www.phpbb.com/community/viewtopic.php?f=6&t=738475&st=0&sk=t&sd=a{,&start={15,30}}
```, but add the backslashes yourself.  (Pasting it into the terminal with the backslashes already there splits it into separate lines.)

---

### Post by peabody on 2008-02-13
That's nice to know, I'm curious when they added this to wget.  I always had to do curl in the past to do batch downloading.

As for the person saying it doesn't work, looks like you may have to put the url in single quotes as & and {} are shell meta characters.  The OP was using windows so didn't have to worry about cmd.exe gobbling those up.

---

### Post by Gadrin on 2008-02-13
Yes, I'm using a DOS window.

Okay a little bit farther with double-quoting & backslash-quoting the Ampersands.

Nice one BTW :)

[COLOR="Blue"]wget -E -k -p -w3 "http://www.phpbb.com/community/viewtopic.php?f=6\&t=738475\&st=0\&sk=t\&sd=a{,\&start={15,30}}"
[/COLOR]
No errors, but I only see one page:

[COLOR="Blue"]viewtopic.php@f=6%5C&t=738475%5C&st=0%5C&sk=t%5C&sd=a{,%5C&start={15,30}}.html[/COLOR]

which is the first one, and **does** have the topic info.

**Are either of you getting all three pages ???**

---

### Post by peabody on 2008-02-13
I just tested it, I only received one page.

It could be that {15,30} is actually specific to cmd.exe.  I've never heard of wget doing batch downloads, always had to do something like:

for ((i=0; i<5; i++)) do wget http://thisplace/$i.jpg; done

We may be observing something windows specific here.

---

### Post by Gadrin on 2008-02-13
well there's this
[I]
So, specifying wget -A gif,jpg will make Wget download only the files ending with gif or jpg, i.e. GIFs and JPEGs.  On the other hand, wget -A "zelazny*196[0-9]*" will download only files beginning with zelazny and containing numbers from 1960 to 1969 anywhere within.  Look up the manual of your shell for a description of how pattern matching works.[/I]

but you'd have to do a recursive retrieval. will that work with topic pages ?

which you might be able to do if you specify  the **t=1234567** for the correct topic number. but that might take a while as it processes the whole site (or a bunch of links in that forum).

most phpBBS use relative links, so I was able to help another guy download a phpBBS site by only following relative links.

---

### Post by Interestedinthepenguin on 2008-02-13
I'm getting all three pages.  

I don't know what could be going wrong.  

I copied and pasted my code (the second one), and added backslashes behind the ampersands.  I am using Cygwin, wget version 1.10.2, and Windows XP (Home).  I don't have to use quotes, either.:?

---

### Post by Gadrin on 2008-02-14
Have you tried a standard DOS window ?

I ran it from my script...
[COLOR="Blue"]
dirchange("J:\Temp Folders\wbtTemp\wGet-Temp\")
comspec = environment("COMSPEC")
cmd = `/c wget -E -k -p -w3 "http://www.phpbb.com/community/viewtopic.php?f=6\&t=738475\&st=0\&sk=t\&sd=a{,\&start={15,30}}"`

runhidewait(comspec, cmd)

message("Debug", "All Done")

exit[/COLOR]

and still get one html file.

I also tried using [ ] instead of braces but the same.

Well more experimentation ahead.

---

### Post by Interestedinthepenguin on 2008-02-14
> **Gadrin said:**
> Have you tried a standard DOS window ?
No, I haven't.  I don't have wget installed in Windows; just Cygwin.  Sorry.  

I assume that you want to figure this out, but would you like me to send you the pages that I've downloaded, instead?

---

### Post by Gadrin on 2008-02-14
oh, no, I believe you. the problem seems to be windows.

what do the filenames look like ? 

mine has the {15,30} in the filename, which I don't think should be happening.

---

### Post by Interestedinthepenguin on 2008-02-14
The (main three) files are named:
[email]viewtopic.php@f=6&t=738475&st=0&sk=t&sd=a&start=15.html[/email]
[email]viewtopic.php@f=6&t=738475&st=0&sk=t&sd=a&start=30.html[/email]
[email]viewtopic.php@f=6&t=738475&st=0&sk=t&sd=a.html[/email]

I didn't know Windows was *that* crippled. lol

I guess it's time for me to learn some DOS.:)

---

### Post by Gadrin on 2008-03-02
Well, I ended up cheating using DOS

```
for %f in (1,15,30) do wget -E -k -p -w3 -PTest -o PHPLog.txt http://www.phpbb.com/community/viewtopic.php?f=6^&t=738475^&st=0^&sk=t^&sd=a^&start=%f
```

according to 
[Windows NT Command Shell]("http://www.microsoft.com/technet/archive/winntas/deploy/shellscr.mspx?mfr=true")

and the FOR documentation...
[FOR construct]("http://technet2.microsoft.com/windowsserver/en/library/44500063-fdaf-4e4f-8dac-476c497a166f1033.mspx?mfr=true")

According to the docs the caret ^ is the correct way to escape the &. However no matter what I tried for the SET (see the FOR docs) it just wouldn't expand correctly on the command line.

One last question: do your navigation links get rewritten as local links/files ? ( the stuff in the box 1, 2, 3).

---

### Post by Interestedinthepenguin on 2008-03-03
> **Gadrin said:**
> [...]do your navigation links get rewritten as local links/files ? ( the stuff in the box 1, 2, 3).

I don't know what you mean by "the stuff in the box", but links to the next page(s) and (some) media in the page(s) _are_ rewritten as local files.

---

