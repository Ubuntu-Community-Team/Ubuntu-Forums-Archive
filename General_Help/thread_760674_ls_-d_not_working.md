---
title: "ls -d not working?"
date: 2008-04-20
forum: General Help
---

### Post by tleave2000 on 2008-04-20
When I type "ls -d" i expect to see only directories listed, but instead i see nothing but a "." listed. Any ideas why? Here's my output for "ls -l" and the for "ls -d":

```
me@me-desktop:~/Desktop/test$ ls -l
total 8
-rw-r--r-- 1 me me    0 2008-04-20 18:17 file_top1.txt
-rw-r--r-- 1 me me    0 2008-04-20 18:17 file_top2.txt
drwxr-xr-x 2 me me 4096 2008-04-20 18:13 folder1
drwxr-xr-x 2 me me 4096 2008-04-20 18:13 folder2
lrwxrwxrwx 1 me me   26 2008-04-20 18:15 Link to folder3 -> /home/me/Desktop/folder3


me@me-desktop:~/Desktop/test$ ls -d
.

```

I thought it would still list the directories: folder1 and folder2 as per the man for ls: 
-d, --directory
              list directory entries instead of contents, and do not dereference  symbolic
              links

In what way have i misunderstood this? Thanks for your input.

---

### Post by Dmole on 2008-04-20
yah I never did understand why it's like that but you could use ```
ls -al | grep ^d
``` to find what you want

---

### Post by tleave2000 on 2008-04-20
Thanks, that's a decent workaround. But i'd still really rather it worked as described. Especially when it's something so basic and fundamental to the command line as ls is. 

I was following this svn article at Dr Dobb's, when i noticed my output didn't match his.
[http://www.ddj.com/linux-open-source/201200496;jsessionid=CB0XGTUWDPXWEQSNDLRSKHSCJUNN2JVN?pgno=2]("http://www.ddj.com/linux-open-source/201200496;jsessionid=CB0XGTUWDPXWEQSNDLRSKHSCJUNN2JVN?pgno=2")
In some ways it's really not a big deal; i can understand the article without it, but it's just one extra layer of confusion to work through. When you're doing something new, that's the last thing you want, and it's something (don't get me wrong, I love Ubuntu and recommend it to everyone), that Ubuntu was supposed to get rid of.. wasn't it?

So although it's not a big deal... it really is, : ) if you see what i mean. Is there a way to make it do it right? Or a really good reason that it shouldn't? I want one or the other : D.
Thanks again to anyone who can answer.

---

### Post by bingoUV on 2008-04-20
You got it all wrong. When you do a **ls <dirName>**, by default the contents of the directory are displayed, not the directory. **ls -d <dirName>** will show the directory instead.

It is working as documented, but the documentation is imperfectly worded, or maybe lacks examples to make it absolutely clear. I am not doc writer myself.

In ls without options, **ls <dirName>**  showing the directory is useless as you already know the directory name, and have a strong suspicion that is exists. So ls assumes you want to know its contents instead. 
But when you add options, like -l, you might want to see the details for the directory instead of files inside it. There **ls -ld** is used.

---

### Post by tleave2000 on 2008-04-20
Aha, thanks, good explanation, and it does tie in with the output in that article.

So the fullstop I was seeing was there because that's the symbol for the current directory.

I guess all that's hard to explain in one line on a man page. Thanks again.

---

