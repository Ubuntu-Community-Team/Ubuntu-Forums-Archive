---
title: "trying to run ./autogen.sh"
date: 2021-07-12
forum: General Help
---

### Post by monaccu on 2021-07-12
[COLOR=#333333][FONT=&quot]I am trying to run this command "./autogen.sh" but it saids access denied.

[/FONT][/COLOR][COLOR=#333333][FONT=&quot]Im trying to change the permission with 775 "sudo chmod -R775 /home/monaccucoin/"[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]buit it will not go through.

[/FONT][/COLOR][COLOR=#333333][FONT=&quot]the files are located in the root folder /monaccucoin/

what would the command be to put in?

Thank you
[/FONT][/COLOR][COLOR=#333333][FONT=&quot]
[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2021-07-12
First where does that come from? What are you  trying to do? More details please.

Secondly why do you use sudo and why are you changing the permission of your entire home directory?

---

### Post by monaccu on 2021-07-12
I am trying to change the permission for the root user, so i can compile a coin with this command "[COLOR=#333333][FONT=Monaco]/autogen.sh" (-bash permission denied.) is the result i get.

i am trying to change the permission with "sudo chmod -R775/home/monaccucoin/"

but the monaccucoin folder is located in the root directory ("root/monaccucoin/")im not sure i i should put home or root?


[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2021-07-13
You only need to make autogen.sh executable (though usually it already is) 

```
chmod +x /path/to/autogen.sh
```

You don't need sudo  and you don't need to change the permission for your entire home and moreover you are so clever that you do it recursively so you just messed up your system. [https://serverfault.com/questions/92420/what-should-be-the-ideal-home-directory-permissions-in-linux](https://serverfault.com/questions/92420/what-should-be-the-ideal-home-directory-permissions-in-linux)

Mind you sub-directories and files inside your home might have different permissions but all that are wiped out by your sudo chmod -R 775

sudo should not be abused, in general you only need to use it if you have to modify system wide file system (like installing software system wide) and this is a reason why it exists. In most cases you stay in your home and there is no reason to use it at all and it is a security problem. If you use sudo all the time there is no point in having it at all.

---

### Post by Impavidus on 2021-07-13
> **monaccu said:**
> [COLOR=#333333][FONT=&amp]I am trying to run this command "./autogen.sh" but it saids access denied.

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]Im trying to change the permission with 775 "sudo chmod -R775 /home/monaccucoin/"[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]buit it will not go through.

[/FONT][/COLOR][COLOR=#333333][FONT=&amp]the files are located in the root folder /monaccucoin/

what would the command be to put in?

Thank you
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

The first command uses a relative path. It doesn't start with a slash. It says: execute the file autogen.sh, which is located in the current directory. The response access denied means that the file is there, but you, the user running the shell, have no permission to execute it.

The second command has several errors. First, there's no need to use sudo when changing permissions on the files you own. Never use sudo when you don't have to. Second, -R means to act on the listed directory and all directories and files therein, which is more than you need and can cause a big mess. Third, there should be a space between -R and 755. If you indeed ran the command without that space, it's good news, because chmod will give an error message and do nothing at all, instead of creating a big mess. Fourth, don't apply the command to your entire home directory if you only want to change permissions of a single file. Never give more permissions that needed.

/home/monaccucoin normally is the home directory of user monaccucoin. /monaccucoin is a directory that only exists if you created it and will be used for whatever you use it for.
> **monaccu said:**
> I am trying to change the permission for the root user, so i can compile a coin with this command "[COLOR=#333333][FONT=Monaco]/autogen.sh" (-bash permission denied.) is the result i get.

i am trying to change the permission with "sudo chmod -R775/home/monaccucoin/"

but the monaccucoin folder is located in the root directory ("root/monaccucoin/")im not sure i i should put home or root?
[/FONT][/COLOR]
The first command contains an absolute path. It starts with a slash. It says: execute the file autogen.sh, which is located in the root directory. The second command misses two spaces, but if you fix it so that it runs, it will create a big mess. root/monaccucoin/ is a relative path, so it will be interpreted relative to the current directory. /root/monaccucoin/ would refer to the monaccucoin directory in root's home directory, /monaccucoin/ to the monaccucoin directory in the root directory and /home/monaccucoin to monaccucoin's home directory.

You get it?

Now, I've got the feeling that you haven't been very accurate with the spaces, dots and slashes in the various commands you posted. Be careful, they make a difference. Pay attention to absolute paths and relative paths. Pay attention to the user's home directory (/home/username/), the root directory (/) and root's home directory (/root/).

Should you put home or root? Well, put in the path where your file is located.

---

### Post by TheFu on 2021-07-13
This free book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) will help learn the basic skills. You are close, but there are some misunderstandings about basic paths that all computers use, including MS-Windows, OSX, and all Unix-like systems.  Perhaps in the point-n-click world, that wasn't important.  It is here and on all Unix systems.  

Being close with a file location isn't sufficient.  1 character wrong and it doesn't work - not at all.

---

