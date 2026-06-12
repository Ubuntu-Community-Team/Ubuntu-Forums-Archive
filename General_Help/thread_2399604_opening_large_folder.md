---
title: "opening large folder"
date: 2018-08-27
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-08-27
hello, I have downloaded a folder that is nearly 130GB of size... However now on my desktop I can not see the pictures inside. When I click on the folder I get a blank page and it just seems to load for a very very long time... Also when I try to get the properties of it all it does is load continously to find the size of it... Does anyone know how I could fix this? Is there a way to open a large folder to see that many pictures and videos and if not how do I split it into smaller folders.

---

### Post by TheFu on 2018-08-27
I wish there were any easy answer. Let's try the easy stuff first.

What program are you using?  You can **turn off thumbnails** in most file managers. Different flavors of Ubuntu use different file managers.   [https://askubuntu.com/questions/518889/how-to-disable-thumbnail-generation](https://askubuntu.com/questions/518889/how-to-disable-thumbnail-generation)   But the release of Ubuntu you are running AND the flavor matters.

How does access work with a shell instead? CLI, shell, terminal all are the same, effectively.  Drop the GUI and you can limit what is displayed at a time.

Having a directory with more than a few hundred files per directory is a bad idea.

To make lots of smaller directories and move the files into them isn't hard.  By alphabet might work ... 
mkdir a ; mv a* a/
mkdir b ; mv b* b/
....
mkdir z ; mv z* z/

You get the idea.  Regex is the pattern matching used almost everywhere in Unix. It is very powerful, but simple when you first start.  
You can also match on the last character .... **ls *4** will match any files/directories that end in 4.  
Or **ls *v** will match any files/directories that end in v, so flv, mkv files will match.  
You can match characters in the middle of files/directories too.  **ls *czr*** will match anything with 'czr' in the middle somewhere.

---

### Post by idkwhatimdoing1.0 on 2018-08-27
that worked... Thank you!

---

### Post by arpitk95 on 2018-08-27
> **idkwhatimdoing1.0 said:**
> that worked... Thank you!

You mind telling us which of the above posted solutions worked for you?

---

### Post by jacksbh on 2018-08-28
> **TheFu said:**
> I wish there were any easy answer. Let's try the easy stuff first.

What program are you using?  You can **turn off thumbnails** in most file managers. Different flavors of Ubuntu use different file managers. [https://askubuntu.com/questions/518889/how-to-disable-thumbnail-generation]("https://how20.com")   But the release of Ubuntu you are running AND the flavor matters.

How does access work with a shell instead? CLI, shell, terminal all are the same, effectively.  Drop the GUI and you can limit what is displayed at a time.

Having a directory with more than a few hundred files per directory is a bad idea.

To make lots of smaller directories and move the files into them isn't hard.  By alphabet might work ... 
mkdir a ; mv a* a/
mkdir b ; mv b* b/
....
mkdir z ; mv z* z/

You get the idea.  Regex is the pattern matching used almost everywhere in Unix. It is very powerful, but simple when you first start.  
You can also match on the last character .... **ls *4** will match any files/directories that end in 4.  
Or **ls *v** will match any files/directories that end in v, so flv, mkv files will match.  
You can match characters in the middle of files/directories too.  **ls *czr*** will match anything with 'czr' in the middle somewhere.


 that is works

---

### Post by TheFu on 2018-08-28
I provided multiple options.  Would be nice to know which of those you used that actually worked.
I'm positive the 2nd one would work, but it is much more work for someone unfamilar with scripting and I didn't actually provide enough details for someone new-to-unix to understand. At least I don't think I did.

Since you never answered the questions asked about the release or file manager program being used, we are all left here wondering.

Our goal isn't to hassle you.  It is so that when the next person sees this thread, she will know what actually worked and be able to use the correct solution without guessing.

---

### Post by idkwhatimdoing1.0 on 2018-08-29
Hello, I used the second method. From the terminal I was able to get into the folder and see all the contents with the function "ls" from there I could select the exact names of the pictures and documents that I needed to move or open. The process isn't hard at all tbh and I consider myself to be quite dumb. From there you could either select the documents you want and then either move them or open them. It takes around 10 minutes to get used to it but after that it's just reputation.

---

### Post by TheFu on 2018-08-29
> **idkwhatimdoing1.0 said:**
> Hello, I used the second method. From the terminal I was able to get into the folder and see all the contents with the function "ls" from there I could select the exact names of the pictures and documents that I needed to move or open. The process isn't hard at all tbh and I consider myself to be quite dumb. From there you could either select the documents you want and then either move them or open them. It takes around 10 minutes to get used to it but after that it's just reputation.

Perhaps repetitive is the word you wanted?

I didn't post a tiny bash script to avoid making the solution less easy to understand, but you could have done a small loop 

```
for i in {a..z} ; do 
   echo $i;
done
```
See how that works?   You can put the mkdir/mv statements after the echo.  Be careful with spacing inside the {}. It matters.

---

### Post by idkwhatimdoing1.0 on 2018-08-30
Yes pretty much that... The moment I dropped the graphics part it went pretty smooth... Any recommendations to find a sweet terminal explanation or practice?

---

### Post by TheFu on 2018-08-30
> **idkwhatimdoing1.0 said:**
> Yes pretty much that... The moment I dropped the graphics part it went pretty smooth... Any recommendations to find a sweet terminal explanation or practice?

No idea what "sweet terminal explanation or practice" means.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) is my best recommendation.
But I learned much of this stuff in the early 1990s. It was a different time.

---

