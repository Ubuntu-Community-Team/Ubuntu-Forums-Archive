---
title: "The meaning of this command"
date: 2016-06-27
forum: General Help
---

### Post by babakflame on 2016-06-27
Dear Fellows

  Can u please help me what does this command mean exactly?

 ```

rm -rf ?.[0-9] [0-9] [0-9][0-9]

```

---

### Post by DuckHook on 2016-06-27
Please explain what is causing you to ask this question.

Any time you invoke any form of:```
rm -rf
```...especially followed by wildcards and globbing, you are juggling with live hand grenades.

rm = remove
-r = recursively into all subdirectories
-f = force. Don't stop for further instructions or give me further warnings.
?.[0-9] = any file whose name is comprised of precisely one character (letter or number) in front of a dot followed by any number
[0-9] = any file comprised of only one number
[0-9][0-9] = any file comprised of only two numbers.

---

### Post by babakflame on 2016-06-27
Dear Duckhook

  Many thanks for your fast reply.

  My question was located at ```
?.[0-9]
``` part. I could not understand its exact meaning. So I asked my question here.


BTW, this command was part of a Allclean file to restart a simulation in ubuntu environment.

  Regards

---

### Post by DuckHook on 2016-06-27
Let me re-phrase: why are you trying to delete a whole bunch of generic files? If you don't want to say, then just tell me it's none of my business, and I will go away without any hard feelings, but I have been around the forums long enough that I am careful about inquiring what users are ultimately trying to do. Sometimes they delete too much and then return with a far bigger emergency trying to recover stuff that they unintentionally deleted.

---

### Post by Bucky Ball on 2016-06-28
What Duckhook is trying to say is don't use rm -rf unless you absolutely, definitely know what you are doing and what you are about to destroy. You should avoid this command. You're actually asking about part of that command that is in the middle, not at the rm -rf part, the part you should be worried about. 

As Duckhook said, please advise what your end-goal is with this as there may be a way safer way of getting there rather than hosing your system.

In short and basically, rm -rf means remove everything that comes after me and everything inside any folder there. In other words, warm up the steamroller and lets flatten and obliterate everything in the direction we've been told to go. :|

---

### Post by DuckHook on 2016-06-28
> **babakflame said:**
> ...this command was part of a Allclean file to restart a simulation in ubuntu environment.I missed your reply because you posted it as an edit rather than as a new post. So, if I understand, you ran a simulation that produces a lot of sequentially numbered files in some directory and now you want to clean out all of the files? Then make absolutely sure you are in the proper directory. The rm command does not ask you if you are sure. It doesn't move things into some trash can. It just immediately and irrevocably does what it is told.

> **Bucky Ball said:**
> What Duckhook is trying to say is don't use rm -rf unless you absolutely, definitely know what you are doing and what you are about to destroy. You should avoid this command. You're actually asking about part of that command that is in the middle, not at the rm -rf part, the part you should be worried about. 

As Duckhook said, please advise what your end-goal is with this as there may be a way safer way of getting there rather than hosing your system.

In short and basically, rm -rf means remove everything that comes after me and everything inside any folder there. In other words, warm up the steamroller and lets flatten and obliterate everything in the direction we've been told to go. :|+1

@OP

BB said this much better than I did. You must be absolutely sure when using this command. There is no going back and no recovery.

---

### Post by bearlake on 2016-06-28
I really hope nobody ran this command to see what would happen before the first response as it sure would have done a lot of damage.

---

### Post by Habitual on 2016-06-28
> **bearlake said:**
> I really hope nobody ran this command to see what would happen before the first response as it sure would have done a lot of damage.
Even my  echo is afraid of that string.

rm = Ruined Machine

---

### Post by babakflame on 2016-06-28
Dear Fellows

  Many thanks for all your replies and comments.

  special thanks for Duckhook

  I am running an OpenFOAM based code and trying to make an Allclean file in bash script so as to run that file for deleting all additional produced files during simulation. I found a sample Allclean file and I was trying to learn all lines of that Allclean file.

  Everything was understandable for me except that line and that part   i.e.    ```
   ?.[0-9]   
```. That's why I asked this question. Just to be able to run my CFD simulation as fast as I can. Also, personally I am interested in learning bash scripts.

  Thats it. All in all, again I appreciate your concerns and helps, especially from Duckhook.


I searched in the net, I could not find any exact help. Every time my last and best place to ask ubuntu (linux) questions is this website.  Thank you all fellows.

  Regards

---

### Post by DuckHook on 2016-06-28
Good luck with your simulations and glad we could help. ;)

You are welcome to ask questions any time.

---

### Post by coldraven on 2016-06-28
Being not too clever I would suggest that at the very beginning of your script you need to change into the correct directory before using rm.

---

