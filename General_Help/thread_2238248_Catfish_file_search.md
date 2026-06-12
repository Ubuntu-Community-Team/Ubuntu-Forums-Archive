---
title: "Catfish file search"
date: 2014-08-06
forum: General Help
---

### Post by gordon99 on 2014-08-06
I have recently installed Xubuntu. When finding my way around I came across Catfish file search. To see how it performed I entered the file name 'applications' which I knew where to find. However, Catfish just displayed the circle of doom. I would have thought that a file searcher would not have any trouble finding 'applications' but, clearly, Catfish did. Am I misusing the program and, if so, what should I have done so that it could locate the 'applications' file.

---

### Post by ibjsb4 on 2014-08-06
[ATTACH=CONFIG]255295[/ATTACH]

Seems to work here :)

---

### Post by pqwoerituytrueiwoq on 2014-08-06
where did you have it searching? (top left of window)

---

### Post by gordon99 on 2014-08-07
Sorry to have to come back on this one. I am using Xbuntu XFCE. As I previously stated, when I typed the file name "applications" (without italics, of course) in the catfish search box I got the circle of doom.

When I closed the program I got a message saying "This window might be busy and is not responding. Do you want to terminate this application". However, I then tried another file and it came up with the necessary information, BUT, there was still a circle of doom on the screen and the "not responding" warning appeared when I closed the application. The file it managed to find is in /home which may, or may not, be significant.

 I then went into Ubuntu Software Centre and removed, then reinstalled, Catfish. The results were exactly the same however.

I would be very grateful if someone could provide suggestions as to what might be wrong and how it can be rectified.

---

### Post by Toz on 2014-08-07
Try running:
```
catfish -vv
```
...from a terminal window and going through the search process. You will get debug messages in the terminal which might help to identify the issue.

---

### Post by gordon99 on 2014-08-07
Thanks Toz, i ran catfish -vv and it produced a number of debug messages. When I tried catfish again it worked. I assume the drop down list is to enable the search to be limited.  If I select "File System", however, then it searches through both operating systems on my dual l boot laptop which makes sense. I will shortly report my question as solved

---

