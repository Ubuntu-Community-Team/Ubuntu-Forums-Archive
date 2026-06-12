---
title: "File System somewhat of a mystery"
date: 2015-03-06
forum: General Help
---

### Post by michael-piziak on 2015-03-06
The filesystem is somewhat of a mystery, where it puts applications and how they're stored.

For example, I searched for "Full Circle Magazine" in terminal using "whereis full circle magazine."   I followed the trail all the way to a file called "full.4.gz"

I expected to find a pdf file at the end of the path.

Attached screenshot.

---

### Post by steeldriver on 2015-03-06
What is "full circle magazine"? how did you download / install it?

The whereis command only looks for **commands** and their manual pages - if "full circle magazine" is a downloaded *file*, it's not going to find it. As well, the command

```

whereis full circle magazine

```

treats each word as a different search term; you would need to have quoted the string (or escaped the spaces)

```

whereis "full circle magazine"

whereis 'full circle magazine'

whereis full\ circle\ magazine

```

Short answer: your search has found the (gzipped) manual page for the [FONT=courier new]full[/FONT] command (likely nothing to do with what you're looking for)

---

### Post by michael-piziak on 2015-03-06
It's the free Ubuntu magazine.  Many issues are available to install from the Software Center.

I just installed issue 59.  Was just wandering where it "physically" ended up.  It's always a pdf file.

You can get the latest issues here:  [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Dennis N on 2015-03-06
Use the Dash in Ubuntu, and search for it there. Entering "full",  it displayed the folder I have them in (Full_Circle_Magazine) and even all the pdfs, even though they have file names like issue_51_en.pdf, not containing the string full.

Where do they end up? When I download them from the web site, they initially go into the folder designated in Firefox for downloads. If you use the software center, not sure where they go, but you can search and find out.

---

### Post by michael-piziak on 2015-03-06
> **Dennis N said:**
> Use the Dash in Ubuntu, and search for it there. Entering "full",  it displayed the folder I have them in (Full_Circle_Magazine) and even all the pdfs, even though they have file names like issue_51_en.pdf, not containing the string full.

Where do they end up? When I download them from the web site, they initially go into the folder designated in Firefox for downloads. If you use the software center, not sure where they go, but you can search and find out.

Explain how you used the dash.  Please give an example.

---

### Post by Linuxratty on 2015-03-06
Here is a video which will show you what to do.

[https://www.youtube.com/watch?v=RWcaH9X9WbI]("https://www.youtube.com/watch?v=RWcaH9X9WbI")

---

### Post by michael-piziak on 2015-03-06
LOL.  I thought he meant to type a - (dash) into terminal.

I know how to use the Dash.   I was just trying to physically figure out where the file actually went.

---

### Post by Holger_Gehrke on 2015-03-07
There are three basic search tools on the command line:
[LIST]
[*]whereis - for finding programs, their source code and manuals 
[*]locate - for finding files. Uses a database that gets updated by a cron-job and for that reason won't find newly created files 
[*]find - the Swiss army knife of search tools. Powerful, complex and - if you're making it crawl all over the file system - not too quick. 
[/LIST]
All of them have manual pages you can read with 'man "command-name"'

But since you got the magazine from the software-center you can just ask the package manager.
```

apt-cache search "Full Circle"

```
gives you the package names and
```

dpkg -L fullcircle-issue-59

```
gives you the files installed for issue 59 of Full Circle Magazine, which should tell you that the PDF resides in '/opt/fullcircle/issues/'.

---

