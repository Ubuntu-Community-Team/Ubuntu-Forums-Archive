---
title: "Newb Question: PHP and Bash, or naw?"
date: 2015-08-05
forum: General Help
---

### Post by joseph62 on 2015-08-05
Hello All,

I'll keep my question as short and clear as possible. I've been interested recently in experimenting with PHP - although I've setup many systems that have used it in the past, as far as actually writing code myself I haven't really have a lot of exposure to it... I do have some decent understanding of Bash and other languages (primarily front-end web stuff) and so in my endeavor to learn, I have found that I acclimate to new syntax faster when actually doing a small project that would need it... So my mini-project is a small networked VM running a LAMP stack, on which I can send and append data to configuration files for differing programs (stuff like fdisk, hdtemp, and other inbuilt utilities).

If there's one thing I've learned in the past, it's that it is harder to re-learn something that you've learned incorrectly than it is to just learn it correctly in the first place... So my question is, in a real life scenario would PHP be appropriate as a medium to transfer user input from a web page to Bash config files on a server/execute said scripts? If so, what would be the most secure and appropriate way to achieve this?

With my limited understanding, as of now the only way I can think of to achieve this is to run PHP that does some sort of sanity check on user input > passes that input on to the Bash files on the server > and then executes those scripts on the server. If for example a script needed root privileges to be executed, what would be a decent way to do this? For instance, one could set UUID on said Bash files for root - but then (if I understand correctly) the application (in this case, php) would have to run as root for execution/editing purposes... I could be wrong but PHP seems like something you should never run as root... Or am I barking up the wrong tree altogether? I know of applications such as Webmin that are written in PHP - so it seems like this usage scenario can be done securely - but to be honest googling the specifics has yet to lend anything that was able to really clear up this matter for me...

Thank you so much for your time, I'm looking forward to your answers, wise sages.

---

### Post by TheFu on 2015-08-06
IMHO.

You should not use PHP for any administrative tasks.  Why?  Because if you aren't an expert, it is to hard to write secure code.

Bash is slow. If speed doesn't matter, fine.

If you want to manage systems, look into a devops tool - something like ansible, puppet, chef. Those tools are specifically designed for this purpose. Most of the config files for a server can be pre-created with just settings like hostname left for some input file to be incorporated. Creating that file from webpage input should be easy.  I would use perl, but someone starting out should probably begin with python which forces good programming practices.

BTW - webmin is perl, not php.

---

### Post by dragonfly41 on 2015-08-06
If you adopt Webmin (which I use for local development) you can create Custom Commands in Webmin menu .. Others > Custom Commands 
and the custom commands can be one liners, multi liners or commands to run bash scripts or other scripts from a custom library. 
Note that the new Authentic Theme is recommended since this allows syntax highlighting.
The new Filemin module is better than the old File Manager module (which is java based and not as nice a GUI).

---

### Post by joseph62 on 2015-08-11
Thank you all so much for the replies, the route I think is the best to take would be the Python route - it's super fast and is often used with a webserver mod for running FastCGI pages... Any thoughts on that? It seems like FastCGI is a pretty common standard for such tasks. Again, thanks so much for your replies, I very much appreciate it. :)

---

### Post by TheFu on 2015-08-11
> **joseph62 said:**
> Thank you all so much for the replies, the route I think is the best to take would be the Python route - it's super fast and is often used with a webserver mod for running FastCGI pages... Any thoughts on that? It seems like FastCGI is a pretty common standard for such tasks. Again, thanks so much for your replies, I very much appreciate it. :)

Modern devs stopped using FastCGI like 10 yrs ago, but if you are just learning, it isn't odd to start with CGI, then FastCGI, then move to a web framework.  Then you'll want/need to learn about security (hopefully before being hacked) - [https://speakerdeck.com/jacobian/python-vs-the-owasp-top-10](https://speakerdeck.com/jacobian/python-vs-the-owasp-top-10)

Being eternally vigilant is a new way of life.

---

### Post by joseph62 on 2015-08-12
On the topic of framework, I took a look at a few and Pylons specifically popped out to me... Security is an ongoing thing, I occasionally do pentest work for some of my clients - even using run of the mill tools it seems that new techniques will always develop faster than security patches for those new techniques... :P

---

