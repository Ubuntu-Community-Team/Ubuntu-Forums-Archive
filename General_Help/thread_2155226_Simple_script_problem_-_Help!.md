---
title: "Simple script problem - Help!"
date: 2013-06-17
forum: General Help
---

### Post by whitesmith on 2013-06-17
I wrote and made the following script executable (chmod +x MyScript.sh):

echo Starting script to launch prog-name.
cd "/home/MyUserName/.wine/drive_c/Program Files (x86)/Prog-Name"
wine prog-name.exe

When I point a terminal at the subdirectory containing the script I type:
./MyScript.sh

And Ubuntu answers:
Starting script to launch prog-name
.
./MyScript.sh: line 2: cd: /home/MyUserName/.wine/drive_c/Program Files
: No such file or directory

Changing the double quotes on line 2 to single ones has no effect. If I put the entirety of line 2 between single quotes, Ubuntu answers:
./MyScript.sh: line 2: cd: /home/MyUserName/.wine/drive_c/Program Files (

I don't see this as being a Wine issue. What the devil is going on? Kudos for any and all help.

---

### Post by Habitual on 2013-06-17
n/m. stated he tried quotes.

---

### Post by whitesmith on 2013-06-17
The mystery deepens. When I escape the spaces (keeping quotes), Ubuntu responds with another letter of the command:
./MyScript.sh: line 2: cd: /home/MyUserName/.wine/drive_c/Program Files (x

I am using Ubuntu 13.04 and Gnome 3.6.3, by the by. I have 32 GB of RAM. I also use Gnome without special effects. Can some guru help me, double pretty please?

---

### Post by whitesmith on 2013-06-17
Deeper still. If I simply escape the spaces and get rid of both single quotes, Ubuntu complains about a syntax error near unexpected token '('.

---

### Post by matt_symes on 2013-06-17
Hi

Open a terminal and type

```
cat -A <file_name>
```

Capital A above and change the filename to the name of your script.

Post the output back here between code tags like this

[noparse]```
output
```[/noparse]

to get output like this.

```
output
```

KInd regards

---

### Post by ajgreeny on 2013-06-17
Where and why did the round bracket come from?

Does the **wine prog-name.exe** command in your script work if you run it directly in terminal from the correct ~/.wine subfolder?

---

### Post by HiImTye on 2013-06-17
you need to escape () as well, however, why it doesn't work with quotes/ticks is a mystery to me
what's the output of```
find $HOME/.wine/ -type d
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by whitesmith on 2013-06-17
[snip]

---

### Post by matt_symes on 2013-06-17
Hi

I think you slightly misunderstood me; my fault as i did not explain myself very well.

I have hoping to see the output of...

```
cat -A Merriam-Webster-Unabridged.sh
```

I'm looking for any characters that should not be there in the script.

Can you post the output of that command above please.

Kind regards

---

### Post by whitesmith on 2013-06-17
> **ajgreeny said:**
> Where and why did the round bracket come from?

Does the **wine prog-name.exe** command in your script work if you run it directly in terminal from the correct ~/.wine subfolder?

Yes! I forgot to escape the parens. I used Main Menu to credate the DT launcher I wanted. Many thanks to all who contributed ideas.

---

