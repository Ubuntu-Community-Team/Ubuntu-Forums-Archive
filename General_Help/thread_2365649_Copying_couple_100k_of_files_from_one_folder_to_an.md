---
title: "Copying couple 100k of files from one folder to another??"
date: 2017-07-08
forum: General Help
---

### Post by toni12 on 2017-07-08
I have folder that contains all the images from my website. It has more than 1M images. It has 3 types for one image: original, thumbnail and small. I only want to copy original images from old directory to a new one. I know the names of all the images I want to copy because I have them stored in DB. So my idea was to fetch all the names from DB using NodeJS and generate .sh script with command that look like this:

cp -n `/path/to/image/{$name}` `/new/images/path/` && \n

But when I run this I get an error "Segmentation fault". I also tried, instead doing "cp" for each image, to include multiple file names as arguments in one cp command, but the I got "Too many arguments" error.

So my question for you is this. How can I copy 333k/1M files (so not every file in dir) from dir to another when I know the names of the files I want to copy??

---

### Post by TheFu on 2017-07-08
Don't use back-ticks.
Your {$name} is incorrect too. "$name" is probably what you want.

However, having more than 1,000 files in a single directory is a really poor web-app design because of the way that file systems are built.

The best way to cp many, many, files depends on the naming convention.  I'm confused. Why bother copying when a move is what is needed to reduce the total number of files in any directory to a reasonable number?

---

### Post by toni12 on 2017-07-09
That code was JS in NodeJS so its correct.

I have more than 1k files in dir because the plugin for Joomla was made that way.

For reasons that take a long time to explain, I have to copy them instead of moving them. 

But I found a solution. In bash. Declare an array with the name of files. In for loop for each name do "cp" command. It works that way.

---

### Post by TheFu on 2017-07-09
Happy you have a solution. Please mark the thread as **solved** to help the community.  
Would be helpful to post part of the resulting script too.

Doing 1 file at a time will be slow.  I'm still thinking **find** or **rsync** would be faster since a copy really is needed (which I can completely accept).

To get the best help for stuff like this, it is usually best to show what you have as input (a sample) and what you need for output (from the sample input), to get the best, relevant answers.

---

### Post by HermanAB on 2017-07-09
Hmm, I agree that with a mass of files it is better to use rsync, since due to the large number something can go wrong.  Rsync can detect errors and correct them, while cp cannot.

---

