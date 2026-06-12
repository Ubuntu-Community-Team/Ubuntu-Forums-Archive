---
title: "How to create a script to add repositories and install apps automatically"
date: 2013-05-28
forum: General Help
---

### Post by brunces on 2013-05-28
Hey, guys.

Please, if possible, I would like to have a little help from you, experts. :)

I want to create a script (bash file) which I will run every time I format a PC and install Ubuntu. I don't know how to code this (that's my doubt), but I'm going to show you, below, an example of I want to do, using "my own words" (instead of codes).

```
#!/bin/sh


echo THIS SCRIPT WILL GUIDE YOU THROUGH THE PROCESS OF INSTALLING APPS.


:Adding_Repository_Pinta
echo Do you want to add the repository for Pinta? (Y,N)
If "N"
GoTo :Adding_Repository_Clementine
If "Y"
sudo add-apt-repository ppa:pinta-maintainers/pinta-stable -y


:Adding_Repository_Clementine
echo Do you want to add the repository for Clementine? (Y,N)
If "N"
GoTo :Adding_Repository_Unsettings
If "Y"
sudo add-apt-repository ppa:me-davidsansome/clementine -y


:Adding_Repository_Unsettings
echo Do you want to add the repository for Unsettings? (Y,N)
If "N"
GoTo :Updating_System
If "Y"
sudo add-apt-repository ppa:diesch/testing -y


:Updating_System
sudo apt-get update


:Installing_Pinta
echo Do you want to install Pinta now? (Y,N)
If "N"
GoTo :Installing_Clementine
If "Y"
sudo apt-get install pinta -y


:Installing_Clementine
echo Do you want to install Clementine now? (Y,N)
If "N"
GoTo :Installing_Unsettings
If "Y"
sudo apt-get install clementine -y


:Installing_Unsettings
echo Do you want to install Unsettings now? (Y,N)
If "N"
GoTo :Exiting_Script
If "Y"
sudo apt-get install unsettings -y


:Exiting_Script
echo All done.

```

(If there are any logic mistakes, please, feel free to correct them as well.)

Now, please, could you tell me how to turn these words into codes? I used to know how to do this in MS-DOS, but Linux is new to me. I really want to learn how to do this. If you can help me, I will really appreciate it.

(Moderators, if this thread is in the wrong room, I apologize. Please, feel free to move it to the correct room. Thank you.)

Thanks in advance, guys.

brunces

---

### Post by Cheesemill on 2013-05-28
I've made a start for you, I'm sure you can figure out the rest....
```
#!/bin/bash

read -p "Add Pinta PPA? (y/n)"
[ "$REPLY" == "y" ] && sudo add-apt-repository -y ppa:pinta-maintainers/pinta-stable

read -p "Add Clementine PPA? (y/n)"
[ "$REPLY" == "y" ] && sudo add-apt-repository -y ppa:me-davidsansome/clementine

read -p "Add Unsettings PPA? (y/n)"
[ "$REPLY" == "y" ] && sudo add-apt-repository -y ppa:diesch/testing


```

---

### Post by Vaphell on 2013-05-28
i'd shove the repo data to associative array to reduce copypasta

```
#!/bin/bash
declare -A repos
repos=(
        [[COLOR="#0000CD"]ppa:pinta-maintainers/pinta-stable[/COLOR]]="[COLOR="#006400"]Pinta[/COLOR]"
        [[COLOR="#0000CD"]ppa:me-davidsansome/clementine[/COLOR]]="[COLOR="#006400"]Clementine[/COLOR]"
        [[COLOR="#0000CD"]ppa:diesch/testing[/COLOR]]="[COLOR="#006400"]Unsettings[/COLOR]"
      )

for [COLOR="#0000CD"]p[/COLOR] in ${!repos[@]}
do
  read -p "Add [COLOR="#006400"]${repos[[COLOR="#0000CD"]$p[/COLOR]]}[/COLOR] PPA? (y/n) " reply
  [ "${reply,,}" = "y" ] && sudo add-apt-repository -y "[COLOR="#0000CD"]$p[/COLOR]"
done
```

---

### Post by brunces on 2013-05-28
Cheesemill,

Thank you very much for your answer. Now, if you don't mind, I just want a final clarification from you, please.

```
#!/bin/bash

# Starting script
echo "This srcipt will guide you through the process of installing apps."
echo "Notice: You can press Ctrl+C at any time to abort the process."


# Adding repository for Pinta
read -p "Do you want to add the repository for Pinta? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-repository -y ppa:pinta-maintainers/pinta-stable


# Adding repository for Clementine
read -p "Do you want to add the repository for Clementine? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-repository -y ppa:me-davidsansome/clementine


# Adding repository for Unsettings
read -p "Do you want to add the repository for Unsettings? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-repository -y ppa:diesch/testing


# Updating system
read -p "Your system will now be updated. Press ENTER to continue."
sudo apt-get update


# Installing Pinta
read -p "Do you want to install Pinta now? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-get -y pinta


# Installing Clementine
read -p "Do you want to install Clementine now? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-get -y clementine


# Installing Unsettings
read -p "Do you want to install Unsettings now? (y,n)"
[ "$REPLY" == "y" ] || [ "$REPLY" == "Y" ] && sudo add-apt-get -y unsettings


# Exiting script
echo "All done."

```

1) What do you think of my code now? Is it functional, clean?
2) I've noticed you changed "#!/bin/sh" to "#!/bin/bash". Does it really make a difference? (I'm asking you this because I also have other scripts like that. Maybe I should change them too.)
3) I've added an option to accept uppercase input (Y) as well. Is that correct or should I do it differently?

Thanks again. You've made my day! (lol) Cheers! :)

brunces

---

### Post by brunces on 2013-05-28
Vaphell,

I'm sorry, I was answering Cheesemill and didn't see your post. That's cool, too.

What about the installations section? Can I use the same code (duplicate it) and change the commands only?

I do appreciate your time spent with me, guys. :)

brunces

---

### Post by Vaphell on 2013-05-28
in case of my code, in order to add repo to the list you only need to modify the repo=() part which makes the script easier to extend than in case of copypasta of the whole **if then** block
**[key]=value** where key is ppa code and value is its description (though it could be reversed, ie desc=key, ppa is the value [desc]=ppa no problem, no difference really )
whatever is there will be used in loop filling repo and description in proper places, i colored them so its clear what lands where.
you can temporarily add some line to the loop that will make it clear how to use arrays, eg **echo "$p = ${repo[$p]}"**
The loop will visit all elements of the array, ask the question for each one and run the repo-add command if condition is met.

as for bash vs sh - sh is leaner but bash much more convenient as it offers many additional features, like the arrays i did use here.

**[ "${reply,,}" = "y" ]** -> ${reply,,} is lowercase(reply) which makes it equivalent to (reply=Y or reply=y)
you could also write it like this: **[ "${reply^^}" = "Y" ]** , ^^ is uppercase for a change.

---

### Post by brunces on 2013-05-28
That's very cool, Vaphell.

I confess, I will have to "study" your code a little. (lol) I mean, I'm new to coding, so... don't get me wrong, please. :)

I got Cheesemill's code easily because he used "my logic", I mean, ways I'm used to dealing with. Lots of copypasta, I know, but something simple for me to understand.

I see your code is very neat and avoids copypasta, indeed. I just have to get used to it and understand its logic, then I'll certainly give it a try.

Anyway, thank you very much for your answer. As soon as I give it a try, I'll post my code here for you to take a look at it and tell me what you think of it, if you don't mind. But, meanwhile, I'll stick with Cheesemill's one. :)

brunces

---

### Post by Vaphell on 2013-05-28
loops are basic programming, they are exactly for such things where you repeat the same thing with only few moving parts that change.
your logic is the same logic i use, the only difference is that i parametrized the moving parts and can have one universal template for everything. Just look at your code, the only places that change in your if blocks are the exact places where i have $p (ppa) and ${repo[$p]} (ppa name)

simple example:
```
$ for p in "a" "b" "c"; do echo "[$p]"; done
[a]
[b]
[c]
$ declare -A repo
$ repo=( [repo1]="desc1" [repo2]="desc2" )
$ for p in "${!repo[@]}"; do echo "[$p]"; done
[repo1]
[repo2]
$ for p in "${!repo[@]}"; do echo "$p (${repo[$p]})"; done 
repo1 (desc1)
repo2 (desc2)
```


*for p in "${!repo[@]}"; do ...; done* means take all keys ( ${**!**repo[@]} ) from the repo array and put them one by one into **p** variable, and then run the code block (do ... done) with that value of p.

---

### Post by brunces on 2013-05-28
Very cool, Vaphell. I will certainly give it a try. Thanks a lot for the clarification. :)

---

### Post by Cheesehead on 2013-05-28
> **brunces said:**
> I want to create a script (bash file) which I will run every time I format a PC and install Ubuntu. I don't know how to code this (that's my doubt), but I'm going to show you, below, an example of I want to do, using "my own words" (instead of codes).

You can do it (non-interactively) using a preseed file instead of a script: [https://help.ubuntu.com/lts/installation-guide/i386/preseed-intro.html](https://help.ubuntu.com/lts/installation-guide/i386/preseed-intro.html)
Preseed files are very handy for multiple or frequent installs. The file is easy to edit when your needs change.

---

