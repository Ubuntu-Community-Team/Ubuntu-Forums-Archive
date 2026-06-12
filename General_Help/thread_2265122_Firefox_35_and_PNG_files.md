---
title: "Firefox 35 and PNG files"
date: 2015-02-12
forum: General Help
---

### Post by John Jason Jordan on 2015-02-12
I have Firefox 35 from Xubuntu repos, which was fresh install  of Xubuntu right after 14.04.1 was released. When I am on a website where there is a link to a PNG image Firefox wants to open the link in Gedit. I can go into Edit > Preferences > Applications, but PNG file type is not listed, and there is no button to add a file type so I can tell Firefox to use some other application as the default. Instead of Gedit I can use the drop-down to select Other, but then Firefox just opens a file browser, rather than presenting me with a list of installed applications. This isn't very helpful, since I don't know where the executable files for my various installed image viewers are, or even what they are called. 

When I click in the link I do have the option to download the file, which I can then open with whatever image viewer I prefer, but that is extra work because I usually do not want to save the image; I just want to view it quickly and move on.

Is there a solution for this problem?

---

### Post by SeijiSensei on 2015-02-12
Let's try a test.  First, make a backup of your bookmarks using Bookmarks > Show All Bookmarks > Import and Backup > Backup.  That will create a file with a .json extension in your home directory.

Now look for the the "hidden" directory called .mozilla under /home/username.  Close Firefox and rename that directory to .mozilla.old.  Now reopen Firefox, and you will have a default installation.  Do you still have the same problem with PNGs?  If so, delete the new .moziila directory and rename .mozilla.old to .mozilla.  The culprit lies elsewhere.

If PNGs display correctly, you can use the same bookmark tool to reimport the json file.  If you have done a lot of customization of Firefox, those changes will be lost, though.

---

### Post by John Jason Jordan on 2015-02-12
> **SeijiSensei said:**
> Let's try a test.  First, make a backup of your bookmarks using Bookmarks > Show All Bookmarks > Import and Backup > Backup.  That will create a file with a .json extension in your home directory.
Now look for the the "hidden" directory called .mozilla under /home/username.  Close Firefox and rename that directory to .mozilla.old.  Now reopen Firefox, and you will have a default installation.  Do you still have the same problem with PNGs?  If so, delete the new .moziila directory and rename .mozilla.old to .mozilla.  The culprit lies elsewhere.
If PNGs display correctly, you can use the same bookmark tool to reimport the json file.  If you have done a lot of customization of Firefox, those changes will be lost, though.

I tried what you suggested, but it was a disaster, mostly because of how I had customized Firefox over the years. In any event, even though the default user interface was horrible, I tried to get to the page that had the link to the PNG file (previously bookmarked) so I could test it but, of course, all my bookmarks were gone. So I tried to import the .json file to get my bookmarks back, but the window to select the html file did not list it, and there was no way to make it display "all files." Apparently is hard coded to display only files that end in .html. (Lame!) So I used my file browser (Thunar) to rename the .json file to .html, and then Firefox allowed me to select it. But after importing it, my bookmarks still fail to appear. 

Eventually I gave up, deleted the new .mozilla folder and renamed the previously renamed one to .mozilla, then ropened Firefox. I am back where I was with no harm done, except to my sanity. 

As an aside, I have another computer with Xubuntu 12.04 and Firefox 31. This version offers only the option to save the file, not to open it. I wonder what happens when other users of Firefox 35 click on a link to a PNG file. Here is a link to one if someone wants to try it out for me:

[http://forums.scribus.net/index.php/topic,1617.msg7118.htm]("http://forums.scribus.net/index.php/topic,1617.msg7118.htm")

---

### Post by monkeybrain20122 on 2015-02-12
A popup appears asking me what to do with the file, it offers to open with vlc, but I can choose others and set it to default so I don't see any problem there. I think sometimes it depends on how the link is actually posted instead of just the content, for example, for most links to .deb FF offers to open with gdebi but for one particular site it offers gedit. I think the problem is with the site rather than FF.

---

### Post by John Jason Jordan on 2015-02-12
> **monkeybrain20122 said:**
> A popup appears asking me what to do with the file, it offers to open with vlc, but I can choose others and set it to default so I don't see any problem there. I think sometimes it depends on how the link is actually posted instead of just the content, for example, for most links to .deb FF offers to open with gdebi but for one particular site it offers gedit. I think the problem is with the site rather than FF.

Thanks for trying it. When I try to choose others I get a file manager, not a list of applications. The file manager would be OK if I knew the name and location of all the executables on my computer. Sadly, that information is hard to find.

---

### Post by monkeybrain20122 on 2015-02-12
The name of the program is eog (eye of gnome) In the drop down choose Open with > Other.. then from the left choose File system, go to /us then /bin then choose from the list eog. Click OK

---

### Post by efflandt on 2015-02-13
The thing is that the links on that page do NOT link directly to png files. If you hover over the links that say .png and look at the bottom of firefox, the links are actually to php scripts. So those .php scripts may be returning an incorrect Content-Type header. For example when I feed those links into wget -S, the reply header for the php script is:```
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Fri, 13 Feb 2015 07:41:07 GMT
  Server: Apache
  X-Powered-By: PHP/5.4.21
  X-Frame-Options: SAMEORIGIN
  X-XSS-Protection: 1
  X-Content-Type-Options: nosniff
  Expires: Mon, 26 Jul 1997 05:00:00 GMT
  Cache-Control: private
  Pragma: no-cache
  Set-Cookie: bb2_screener_=1423813267+75.49.210.43; path=http://forums.scribus.net
  Last-Modified: Fri, 13 Feb 2015 07:41:07 GMT
  Vary: Accept-Encoding
  Keep-Alive: timeout=15, max=100
  Connection: Keep-Alive
  Transfer-Encoding: chunked
  Content-Type: text/html; charset=UTF-8
Length: unspecified [text/html]
```Notice the **Content-Type: text/html; charset=UTF-8**. But I do not know what it does from there when returning the actual image content.

That may not be an issue for Internet Explorer which mostly ignores Content-Type, and totally ignored that while being developed by college students as Mosaic beta 20 years ago. But a compliant browser like firefox can be confused by incorrect Content-Type headers. For example if you open a .png file on your own computer with firefox, it should have no problem at all doing that. So I suspect that it is the php scripts that are broken by clueless Windows users, not your browser settings.

---

### Post by Holger_Gehrke on 2015-02-13
> **efflandt said:**
> The thing is that the links on that page do NOT link directly to png files. If you hover over the links that say .png and look at the bottom of firefox, the links are actually to php scripts. So those .php scripts may be returning an incorrect Content-Type header. For example when I feed those links into wget -S, the reply header for the php script is:

 ... snip ...
> **efflandt said:**
> 
Notice the **Content-Type: text/html; charset=UTF-8**. But I do not know what it does from there when returning the actual image content.

That may not be an issue for Internet Explorer which mostly ignores Content-Type, and totally ignored that while being developed by college students as Mosaic beta 20 years ago. But a compliant browser like firefox can be confused by incorrect Content-Type headers. For example if you open a .png file on your own computer with firefox, it should have no problem at all doing that. So I suspect that it is the php scripts that are broken by clueless Windows users, not your browser settings.

Sorry, but you forgot to escape the semicolons in the address. If you do (or enclose the whole address in single quotes) the headers you get are:
```

  HTTP/1.1 200 OK
  Date: Fri, 13 Feb 2015 09:42:16 GMT
  Server: Apache
  X-Powered-By: PHP/5.4.21
  X-Frame-Options: SAMEORIGIN
  X-XSS-Protection: 1
  X-Content-Type-Options: nosniff
  Expires: Sat, 13 Feb 2016 09:42:17 GMT
  Cache-Control: no-cache
  Pragma: 
  Set-Cookie: bb2_screener_=1423820537+79.194.66.156; path=http://forums.scribus.net
  Content-Encoding: none
  Content-Transfer-Encoding: binary
  Last-Modified: Tue, 10 Feb 2015 20:56:54 GMT
  Accept-Ranges: bytes
  Connection: close
  ETag: "1160Auswahl_011.png1423601814"
  **Content-Disposition: attachment; filename="Auswahl_011.png"**
  Transfer-Encoding: chunked
  **Content-Type: application/octet-stream**

```

If you **do** forget the quoting, you get the **html-page** of the forum (the stuff after the semicolon is treated as new shell commands, you have some new variables in your environment), so the headers are **right**. The 'Content-Disposition' header is the one responsible for getting a 'open-or-save' dialog, the 'Content-Type' basically says "some kind of application specific binary, I don't know what it is".

Anyways, the whole thing is a bit academic - at least for this forum-address - since a click on the thumbnail above the link either enlarges the thumbnail in the browser if the image is small or opens a pop-up with the image at full size.

---

### Post by Holger_Gehrke on 2015-02-13
> **John Jason Jordan said:**
> 
As an aside, I have another computer with Xubuntu 12.04 and Firefox 31. This version offers only the option to save the file, not to open it. I wonder what happens when other users of Firefox 35 click on a link to a PNG file. Here is a link to one if someone wants to try it out for me:

[http://forums.scribus.net/index.php/topic,1617.msg7118.htm](http://forums.scribus.net/index.php/topic,1617.msg7118.htm)

I think you misunderstood the way that forum is supposed to work. You click the **thumbnail** to view the image and the **link** to save it.

---

### Post by SeijiSensei on 2015-02-13
I'm using 35.0.1 and those images display correctly inline.  I've never used a version of Firefox that didn't display PNG files correctly.

---

