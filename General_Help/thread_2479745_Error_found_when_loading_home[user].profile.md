---
title: "Error found when loading /home/[user]/.profile"
date: 2022-10-05
forum: General Help
---

### Post by inillemra on 2022-10-05
Hi all, I'm on Ubuntu 22.04.1 LTS and i get this error when i log in my profile, it doesn't really affect much as i can still do everything just fine but i'd still like to solve this

This is the full error message:

Error found when loading /home/[user]/.profile 

/home/[user]/.profile: line 18 .: .: is a directory

As a result the session will not be configured correctly.
You should fix the problem as soon as feasible.

And that's it.

This is what's written in .profile from line 18 to the last line:

18 . . .
19 export PATH=$PATH:/usr/local/go/bin
20 # set PATH so it includes user's private bin if it exists
21 if [ -d "$HOME/bin" ] ; then
22       PATH="$HOME/bin:$PATH"
23 fi
24 
25 # set PATH so it includes user's private bin if it exists
26 if [ -d "$HOME/.local/bin" ] ; then
27        PATH="$HOME/.local/bin:$PATH"
28 fi

I should also add that i recently installed the latest version of GO for my future degree lessons.

I'm new to Ubuntu, so if you can teach me how to solve this i'd be really thankful.

---

### Post by &amp;KyT$0P# on 2022-10-05
> **inillemra said:**
> 18 . . .

This line is the reason for the error.  It is attempting to run the current working directory as a program, with the first and second arguments to this "program" also being the current working directory.  What were you trying to achieve by doing this?

---

### Post by inillemra on 2022-10-05
> **halogen2 said:**
> What were you trying to achieve by doing this?

Nothing, i didn't put this line in, i think it has something to do with the go installation since line 19 is a go directory? Idk as i said i'm new to all this. 

Thanks for the reply

---

### Post by &amp;KyT$0P# on 2022-10-05
In that case, if you just delete that line does the error resolve and your [FONT=Courier New]~/.profile[/FONT] behave as expected?

---

### Post by Impavidus on 2022-10-06
> **halogen2 said:**
> This line is the reason for the error.  It is attempting to run the current working directory as a program, with the first and second arguments to this "program" also being the current working directory.  What were you trying to achieve by doing this?

Actually, it tries to source the current directory, not run it. It's equally impossible.

---

### Post by inillemra on 2022-10-07
> **halogen2 said:**
> In that case, if you just delete that line does the error resolve and your [FONT=Courier New]~/.profile[/FONT] behave as expected?

Yes, it did resolve the issue, thank you and sorry for the late reply

---

