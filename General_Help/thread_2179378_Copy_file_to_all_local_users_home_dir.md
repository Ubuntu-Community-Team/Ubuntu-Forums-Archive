---
title: "Copy file to all local users home dir"
date: 2013-10-08
forum: General Help
---

### Post by z-stephen-davis on 2013-10-08
I have a few users on my system and rather than manually copy this file to every user I am trying to do it with a command. 
The file is in my home dir so the command that I type is 
```
sudo cp TextFile.txt /home/*/
```
When I do that I get 
```
cp: omitting directory '/home/user1/'
cp: omitting directory '/home/user2/'
cp: omitting directory '/home/user3/'
```
and so on. 

Can anyone tell me what I am doing wrong? or what else I need to do. 

I also ran chmod 644 against the file so everyone could read it.

---

### Post by sisco311 on 2013-10-08
Hi and welcome to the forums!

You can't specify multiple target directories. You can use a for loop to copy the file in each directory:
```

for dir in /home/*/
do
    sudo cp -- ./filename "$dir"
done

```

If you also want to change the ownership of the copies, then you could parse the /etc/passwd file in order to get the home directories and user names:
```

while IFS=: read -r user _ uid gid _ home _
do
    if (( uid >= 1000 ))
    then
        **echo** sudo cp -- ./filename "$home"
        **echo** sudo chown "${uid}:${gid}" "${home}"/filename
    fi
done < /etc/passwd

```

If you have any questions feel free to ask.

---

### Post by z-stephen-davis on 2013-10-08
Thanks for the help, it worked like a charm.
I only need them to be able to read the file so I used your first script. 
I will have to save the other one as it may come in handy later on.

---

