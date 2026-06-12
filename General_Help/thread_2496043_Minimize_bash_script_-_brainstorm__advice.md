---
title: "Minimize bash script - brainstorm / advice"
date: 2024-03-12
forum: General Help
---

### Post by Drenriza on 2024-03-12
Hi All
I am seeking some advice / brainstorm.

Currently i am creating a bash script that needs to be deployed on a server that only allow the script to be 16KB large, maximum.

The script is getting a bit large so i was wondering if there was some minimize tricks like we know them from HTML and CSS.

Are there a common function one could create, and parse the script through to remove all unnecessary whitespaces, newlines etc ?
Besides just writing better scripts ;)

Thank you in advance
Best regards

---

### Post by MAFoElffen on 2024-03-12
Without seeing the code of the script, I cannot answer.

Seems your scripts are limited to 16384 characters.

There used to be a Linux kernel limit way back when, where a line was limited to 80 characters long. A lot of us old timers still try to hold to that in our coding, as a rule of thumb. That would put your limit to around 204 lines per script...

I create variables and functions. Both for reduction of characters, reproduction of redundant typing, and ease of maintenance where things are changed. Where things repeat, decide if it should be a variable or function.

Then if you create external scripts that can be called, passing variables to functions, then your individual script sizes can be reduced. Keep in mind, if you do that, it will use more memory with each script (during it's execution)...

My scripts are a lot larger than 16K. That comes from having spent time previously as a maintenance programmer. If your shop is limited at that size... Bring up some points from my past experience, where  I would have to try to figure out where something was broken that usually already had 10 patches applied to it, and nothing was commented or documented. Hard to trace through the logic without that.

Later, teaching Computer Science, I impressed upon students the importance of indentation, formatting, and extensive comments to make their code easy to read and follow. (Even if the conventions did not require that!!!) That is should read like a book. Production scripts have "a life". They live beyond their initial release. They should be easy to understand, and maintain.

---

### Post by dragonfly41 on 2024-03-12
Can they be compressed ?

[https://ilearnedhowto.wordpress.com/2018/09/12/how-to-create-compressed-and-or-encrypted-bash-scripts/](https://ilearnedhowto.wordpress.com/2018/09/12/how-to-create-compressed-and-or-encrypted-bash-scripts/)
[https://github.com/dealfonso/lsc](https://github.com/dealfonso/lsc)

---

### Post by Tadaen_Sylvermane on 2024-03-12
You can cut the size of the name of your variables and function names. That should gain a surprising amount  of characters depending on how often those variables and functions are used. Maybe keep a separate file or man page for commenting / explanation. Remove them from the script. Neither are particular good ideas because they will make the script harder to read but 16k is an awful small space to work with. Something has to give.

---

### Post by MAFoElffen on 2024-03-13
Back in the early 90's, in the company I worked for at the time, I pushed for using code libraries of functions... Per se, later called API's. These were common functions to do things. The more we did, they got added to that library.

That way, code was streamlined, and had to just call that library. That grew into other libraries, handling other things... So that things initially got separated into business rules, data handling, and user interfaces. Then grew more. Each was kept as small pieces of the larger puzzle.

I touched on that in my last post.

You could always remove most of your whitespace, shorten names to a minimum, no comments and write it all in one line. That will run. But good luck if there is any problem with it, and someone else has to debug, change or in any way maintain it. Just because that "is possible", does not make that a good idea at all. That is just not a best practice in any remote kind of way. That does not make business sense, nor common sense..

These days, 1MB is more realistic. My system-info script is currently almost 2700 lines and is about 87k. It used to be said if a script is over 1MB, you should consider rewriting it programming language that is compilable. But it depends...

Most people don't realize that you can compile BASH scripts with 'shc' ([Ubuntu manpage shc]("https://manpages.ubuntu.com/manpages/jammy/man1/shc.1.html"))... But using my 'system-info' script as an example, the script source is 87k. Compiled with shc as a binary, it is 122k. <-- Not what you would expect, right? The math doesn't always work out.

There is no limit to how large  a BASH script can be. (Or other scripting languages for that matter.) If you look at the 'system-info' script, you can see how I tuned it to release variables to save, release and recovery memory after each function has run... There are ways to make things run faster, and more efficient. I've had production maintenance scripts that were over 100MB and ran for 20 hours, with no problems... It's really just limited to our imagination.

---

### Post by ActionParsnip on 2024-03-13
Is it just one file that can't be over a certain size or is it the entire run environment? You could make smaller scripts that run sections of the code and then call them (Kinda like a function). Each script would be the size you like, or smaller. You'd just be breaking a larger script into smaller scripts to work around the constraint but should work. You may need to use variables to pass things between them as each script won't retain the variables from the parent script (or use a text file in /tmp to store stuff, but that's a bit hacky)

---

### Post by MAFoElffen on 2024-03-13
We are still talking about generalizations... 

I go back to the first sentence of my initial response, and further ask for an example of your script... Or at least a goal to shoot for.

Then we can bite into what we can see. Actually apply methods that might be able to shrink it's footprint.

---

