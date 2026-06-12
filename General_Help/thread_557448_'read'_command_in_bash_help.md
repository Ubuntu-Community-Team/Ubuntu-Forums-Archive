---
title: "'read' command in bash help"
date: 2007-09-22
forum: General Help
---

### Post by nb123 on 2007-09-22
Hi, I'm having a problem with my read command in a bash script. When I use it in a regular way like this :--- 
```

read asdf
echo $asdf

```

It accepts '/home/myname/My\ Videos' for an input for variable asdf. It interprets this correctly as '/home/myname/My Videos'.

However, when I do the following: ---

```

folder=0
until [ -e $folder ]; do
       read folder
       if [ -e $folder ]; then
	     break 2
	else
             mkdir -pv $folder
	     if [-e $folder ]; then
		   break 3
             else
	           echo -e "\nPlease enter a valid folder extension:---"
             fi	        
         fi   
done

```

(Note: this is part of an even larger loop, thus the break 2 & break 3 commands) 

It does not allow me to input any folder extension like '/home/myname/My\ Videos' with spaces in it. It gives me an error saying: ---

```

./recorddesk.sh: line 34: [: /home/myname/My: binary operator expected
mkdir: created directory `/home/myname/My'
mkdir: created directory `Videos'
./recorddesk.sh: line 38: [-e: command not found
Please enter a valid folder extension:---
./recorddesk.sh: line 32: [: /home/myname/My: binary operator expected

```

Why does this happen?

---

### Post by nb123 on 2007-09-22
Oh wait, never mind, I just realized why, because it's not interpreting the value of the variable folder, so I need to do

if [ -e "$folder" ] 

instead of just 

if [ -e $folder ]

---

