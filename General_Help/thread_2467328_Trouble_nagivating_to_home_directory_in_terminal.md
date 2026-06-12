---
title: "Trouble nagivating to /home directory in terminal"
date: 2021-09-23
forum: General Help
---

### Post by ishwashere on 2021-09-23
I used the cd to change my current directory with error. So I inputted the -ls command with the same result. Do I have to elevate to superuser su or need to use a different command? 


I attached a screenshot of my terminal window.

---

### Post by coffeecat on 2021-09-23
Both...

```
cd /home/desktop
```

and

```
cd /Home/Desktop
```

are wrong. Linux is case sensitive. It should be:

```
cd /home/*username*/Desktop
```

Also:

```
cd /home/*username*/Downloads
```

By the way, please do not post screenshots of the terminal. It is near impossible to read. If you want to post terminal output, simply highlight with the mouse however much you want to include in your post, right-click -> copy, and then paste into your post, not forgetting to enclose the pasted terminal output between BBCode code tags (link in my sig if you need it). 

By the way 2: elevating to superuser in this situation is a bad idea. If you are doing something wrong, elevating to superuser will simply make it easier to do severe damage to your system.

---

### Post by deadflowr on 2021-09-23
You were already in home.
The ~ symbol is symbolic of your home directory.
You did however move into the /var/log directory.
To move back to home simply run cd without anything else.
use the command
```
pwd
```
to see where you are currently in the system.
Once back in home try using ```
ls
``` to see the proper directory names.
Common directories like Pictures and Desktop begin with Capitalized letters.
Most other directories will be all small letters.

---

### Post by Dennis N on 2021-09-23
> **ishwashere said:**
> I used the cd to change my current directory with error. So I inputted the -ls command with the same result. Do I have to elevate to superuser su or need to use a different command? 


I attached a screenshot of my terminal window.
To navigate to your home directory, realize that:
**/home** is not your home directory. It's actually **/home/<username>**, meaning it's  **/home/ishmael** for the user in your screenshot.
Your Desktop would be:
```
/home/ishmael/Desktop
```
Your home directory has a special symbol as mentioned. So your Desktop could also be named: 
```
~/Desktop
```

---

### Post by The Cog on 2021-09-23
As others have pointed out, the home directory is lower case "/home", not "/Home".
But that's not **your** home directory. That's the directory that holds all user's home directories. As your username is ishmael then there will be a /home/ishmael directory, and it is **that** directory that is **your** home directory. So your Downloads directory will be /home/ishmael/Downloads. 
To get to your home directory, you can use the '~' symbol, and to get into your Downloads you can do "cd ~/Downloads".

---

### Post by TheFu on 2021-09-23
Linux (and all Unix-based OSes) are multi-user.  All commands have a userid connected and the HOME for each user is a known thing if there is a login for that user.  This is stored in the POSIX passwd entry for each userid.

After you login, the userid is placed into the HOME for that userid.  There are a number of equivalent ways to change directory to the HOME for any userid, but getting to the HOME for the current userid is really easy.  Assuming 'bash' as the shell (there are 20-50 different shell commands possible, like command.com or cmd.exe or 4NT.exe on MS-Windows), we can get to the current userid's HOME using any of these commands ... they work from anywhere, regardless of the current working directory - cwd/pwd.

[LIST]
[*]cd
[*]cd ~
[*]cd $HOME
[/LIST]

each of those are equivalent for the current userid.

To get to a different userid's HOME, just use ~{username}.  To if the userid is "thefu", 
```
cd ~thefu
```
That would work both for any other user on the system AND for "thefu", just like the 3 commands listed above.  This all assumes the directory permissions for ~thefu (or $HOME) allow another userid access.  Some users lock access to their HOME directories from other users or to users who aren't in their group.  Power to the user!

---

### Post by psychohermit on 2021-09-25
If you had done ```
 ls / 
``` you would have seen that home is all lower case.

```

glenn@Psycho:~$ ls / 
bin    dev   lib    libx32      mnt   root  snap      sys  var 
boot   etc   lib32  lost+found  opt   run   srv       tmp 
cdrom  home  lib64  media       proc  sbin  swapfile  usr 

```

Then ```
ls /home
``` would have shown your username

```

glenn@Psycho:~$ ls /home 
glenn  lost+found  ubuntu 

```

--glenn

---

