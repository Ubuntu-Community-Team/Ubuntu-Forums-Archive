---
title: "Windows Virus in Ubuntu"
date: 2006-10-24
forum: General Help
---

### Post by Morpheus747 on 2006-10-24
I think I may have done something stupid. In fact, I'm sure I did :-)

I downloaded some file via the edonkey network (legal content, of course :)) and found a (MS Windows) setup program (setup.exe). It looked pretty legit, so I thought I'd see if it worked or not through Wine. After I ran it I got the following message:

> 
      PRE-INSTALL v1.07
      (C) pUcE Software 2006
      Pre-install has checked your config.
      Everything is ok, you can now run the setup program
      Enjoy!


This looked pretty suspicious, so I googled it. Sure enough, it's a virus: *W32.Ecup*. See here: 

[http://www.symantec.com/security_response/writeup.jsp?docid=2006-053111-0818-99&tabid=2](http://www.symantec.com/security_response/writeup.jsp?docid=2006-053111-0818-99&tabid=2)

In effect, I've released an emulated Windows virus on my Ubuntu box ](*,) 

I proceeded to kill all wine tasks (just in case the virus was still running), uninstalled Wine completely and removed my ~/.wine folder. Prior to doing so, I did see that the virus had copied itself to ~/.wine/drive_c/windows/temp/svchost.exe (as described on the symantic page).

Now, I'm really worried here. Is it possible that the virus has infected my Ubuntu box or was it restricted to the emulated environment of Wine? I did see, however, that the file had created a log.txt file on my desktop (~/Desktop), so it did reach outside of the Wine folder (~/.wine/drive_c)!

Does anyone have any advice on how to make sure my box is safe and/or how to put my mind at ease?

---

### Post by MJSOnline on 2006-10-24
Good question.  I too would like to know the answer to this.  M

---

### Post by Pelekophori on 2006-10-24
As I understand it, without wine to run it Linux has no way of understanding the virus' code.  When the virus tries to infect windows program/process x, Linux will go wtf? It won't have the necessary programs running that the virus wants to get at.  

Even if it did, all the critical Linux files are protected by requiring you to have root permissions to alter.  Hopefully you wouldn't run random executables with sudo :mrgreen:

---

### Post by ehird on 2006-10-24
linux.com tested viruses on wine sometime - basically, they can't do much even on the worst cases.

---

### Post by Morpheus747 on 2006-10-24
Ok, thanks for the responses. Fortunately, I didn't run it as root. Still, is there anything that remains of Wine once it is uninstalled (via synaptic) and the ~/.wine dir has been removed?

I might want to re-install wine someday, but I'd hate to see the virus pop back up, due to some part of wine's configuration that I forgot to remove.

---

### Post by Rhubarb on 2006-10-24
If you delete your ~/.wine directory, the virus and your emulated drive cd should be wiped.
Then just type in wine in the terminal to re-create ~/.wine again.

I don't think that it's even necessary to remove / reinstall wine.

---

### Post by Morpheus747 on 2006-10-24
> **ehird said:**
> linux.com tested viruses on wine sometime - basically, they can't do much even on the worst cases.

Yeah, there's an article here: [http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

It's really quite funny :P


> **Rhubarb said:**
> If you delete your ~/.wine directory, the virus and your emulated drive cd should be wiped.
Then just type in wine in the terminal to re-create ~/.wine again.

I don't think that it's even necessary to remove / reinstall wine.

Thanks, now I can sleep easier, knowing my ubuntu box is secure. :)

---

### Post by hashimoto on 2006-10-24
*Too late*
I would say you are quire safe. A bit old, but:
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by Rhubarb on 2006-10-24
"Creates the file %CurrentFolder%\log.txt and opens it, displaying the following text:"
I'm guessing wine told the virus program that your current folder was z:\home\username\Desktop\
That's why the log file is there on the desktop, it would have write access to it.
By the looks of it, you should've removed all traces of the virus, as the ~/.wine directory also contains the registry.

---

