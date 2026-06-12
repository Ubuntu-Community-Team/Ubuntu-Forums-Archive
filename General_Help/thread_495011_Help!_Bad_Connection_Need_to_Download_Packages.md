---
title: "Help! Bad Connection Need to Download Packages"
date: 2007-07-07
forum: General Help
---

### Post by Nimaran on 2007-07-07
I don't yet have an internet connection in Linux, but I need to download some  paclages. I know how to download packages on a Windows computer from the manager, but I have attempted to reload the manager so my repositories are no longer up to date, and therefore can't update my packages or download any new ones. Is there a way to download Package Repositories in Windows then upload them into the manager? Thank You in advance for your help.

---

### Post by southernman on 2007-07-08
Try this

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")
[http://ubuntuforums.org/archive/index.php/t-419441.html]("http://ubuntuforums.org/archive/index.php/t-419441.html")

This is the google link I used to grab the above. 

[http://www.google.com/search?q=download+ubuntu+repository+to+a+cd%2Fdvd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a]("http://www.google.com/search?q=download+ubuntu+repository+to+a+cd%2Fdvd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

You might also try seaching the forums. I've seen this answered before... just didn't save the links.

---

### Post by Nimaran on 2007-07-08
AptonCD would work great. The only problem is my only other computer connected to the internet is running Windows, so that won't work. Is there anything else we can do? I don't need to actually download the .deb files I found a way to do that from a Windows machine. I just need to find a way to update the files in the repos without an internet connection. Any help would be great.

Thank you

This post told me how to download from Windows (Lost Link here is a copy/paste)
>  Re: How can I install package without network!
If the program you want shows up in synaptic when you search, this should work fine.

Run Synaptic, and go to the File menu. In there you will find 'Generate package download script'. So, select all the packages you want to install and generate the script.

Take that script to a linux computer connected to the internet (I will explain windows way too). Put the script in a new folder because it will download lots of files. Remove the script file after you've downloaded everything.

Once you've got the files back to your computer, go to the file menu in synaptic again. In there is a option called 'Add downloaded packages'. Click that and open the folder which contains the deb files. Remember, it will complain if you have anything other than the deb files in that folder!

For Windows.
Generate the script as per usual. Open the script in gedit, click on 'Replace' Icon. Enter these:
In the search for box:
wget -c
In the replace with box:
<a href="

Click the Replace All button. Repeat the replace with these two:
Search for:
.deb
Replace with:
.deb" >Package link</a><br>

Replace the first line with this text:

<html><head></head><body>

And add this line to the bottom
</body></html>

Now you can save that file as a .html file and use it in windows.

See, but the problem is not all the packages are showing up in the manager.

---

### Post by Nimaran on 2007-07-08
Never mind on this problem I got my Internet working, but it might be good for other people if we can figure this out. Thanks for your willingness to help. :)

---

