---
title: "Why screenshots are inaccessible from Windows?"
date: 2014-02-19
forum: General Help
---

### Post by Anand.Kumar on 2014-02-19
Yesterday, I took a few screenshots from Ubuntu 13.10. I used the default application and saved the file to Windows NTFS partition. Actually, it's a dual boot pc having Win 7 and Ubuntu 13.10. 

This is surprising to see that the screenshot are accessible from Ubuntu but not from Windows. You might like to take a look on the screenshot. (The property seems interesting to me!)

How do i getting rid of this thing?

Thanks in advance

[ATTACH=CONFIG]250477[/ATTACH]

---

### Post by Bucky Ball on 2014-02-19
Know nothing about the properties but if your pics are on a Linux partition, i.e. an EXT* partition, Win cannot read them. Most people create a NTFS partition if they're intending to share data with Win which can be read/written to by both Ubuntu and Win.

If they're already on an NTFS partition and work fine in Ubuntu but not Win, then this is probably not a Ubuntu question. ;)

---

### Post by fdrake on 2014-02-19
are you able to see the pics if you open it as an Admin?

---

### Post by monkeybrain20122 on 2014-02-19
This is really a Windows problem that you should ask in a Windows forum. But it took me only one second of googling to find this
[http://answers.microsoft.com/en-us/windows/forum/windows_7-pictures/windows-photo-viewer-stopped-opening-png-files/a8db9335-2278-4058-807e-894143f9518b](http://answers.microsoft.com/en-us/windows/forum/windows_7-pictures/windows-photo-viewer-stopped-opening-png-files/a8db9335-2278-4058-807e-894143f9518b)

---

### Post by Anand.Kumar on 2014-02-19
OK. It is so easy to fix that. I just renamed the file to something else and it worked. The file name should not have "[FONT=courier new]:"[/FONT]

Here is the explanation: [http://technet.microsoft.com/library/Cc956689](http://technet.microsoft.com/library/Cc956689)
> [COLOR=#2A2A2A][FONT=Segoe UI]The filename, directory name, or volume label syntax is incorrect.
[/FONT][/COLOR][COLOR=#2A2A2A][FONT=Segoe UI][B]
Explanation:
[/B][/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]The system does not accept the keyboard combination Alt+0 through Alt+32 or the following characters: \\ \\ / [ ] : | < > + ; = . ? "[/FONT][/COLOR]

> **monkeybrain20122 said:**
> This is really a Windows problem that you should ask in a Windows forum. But it took me only one second of googling to find this
[http://answers.microsoft.com/en-us/windows/forum/windows_7-pictures/windows-photo-viewer-stopped-opening-png-files/a8db9335-2278-4058-807e-894143f9518b](http://answers.microsoft.com/en-us/windows/forum/windows_7-pictures/windows-photo-viewer-stopped-opening-png-files/a8db9335-2278-4058-807e-894143f9518b)
This is not the situation I had. thx btw.


Thank you all!!

---

### Post by Bucky Ball on 2014-02-19
Please mark thread as solved to help others by following the instructions in the link in my signature. Thanks.

---

