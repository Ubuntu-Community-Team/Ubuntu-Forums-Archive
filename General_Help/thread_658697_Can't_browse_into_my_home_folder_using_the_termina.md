---
title: "Can't browse into my home folder using the terminal!!!!"
date: 2008-01-04
forum: General Help
---

### Post by Del Piero on 2008-01-04
Just had installed Ubuntu Gutsy and i got to the business of customizing my softwares etc...Anyway using the terminal to browse my home directory isn't working!!! am i missing something? did something change or what?

> 
omar@Megatron:~$ cd /home
omar@Megatron:/home$ cd/omar
bash: cd/omar: No such file or directory
omar@Megatron:/home$ dir
omar
omar@Megatron:/home$ cd omar
omar@Megatron:~$ cd /home/omar
omar@Megatron:~$ cd /home
omar@Megatron:/home$ chmod a+x .conky_start.sh
chmod: cannot access `.conky_start.sh': No such file or directory
omar@Megatron:/home$ omar
bash: omar: command not found
omar@Megatron:/home$ cd omar
omar@Megatron:~$ cd omar
bash: cd: omar: No such file or directory
omar@Megatron:~$ cd /omar
bash: cd: /omar: No such file or directory
omar@Megatron:~$ cd /home
omar@Megatron:/home$ dir
omar
omar@Megatron:/home$ omar
bash: omar: command not found
omar@Megatron:/home$ open omar
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console
omar@Megatron:/home$ browse omar
bash: browse: command not found
omar@Megatron:/home$ cd omar
omar@Megatron:~$ 

---

### Post by PeterJS on 2008-01-04
```

omar@Megatron:~$ cd /home

```Worked just like it should, you are now in /home which has a subdir omar
```

omar@Megatron:/home$ cd/omar
bash: cd/omar: No such file or directory

```This didn't work because: 1) you need a space between cd and it's target 2) there's no /omar, what you wanted was /home/omar, which from home is referred to as just omar
```

omar@Megatron:/home$ dir
omar

```No surprise here, ls is more commonly used and more useful in general
```

omar@Megatron:/home$ cd omar

```Yep this worked just like it should have and is what your first attempt should have been,
```

omar@Megatron:~$ cd /home/omar

```
Yep that worked, you moved from /home/omar to /home/omar
```

omar@Megatron:~$ cd /home

```Worked just like it should, you are now in /home which has a subdir omar
```

omar@Megatron:/home$ chmod a+x .conky_start.sh
chmod: cannot access `.conky_start.sh': No such file or directory

```/home isn't you home directory, /home houses the home directory of all the users on the machine, so the file you were looking for was most likely in /home/omar, but definitely not /home
```

omar@Megatron:/home$ omar
bash: omar: command not found

```Again no surprise that that didn't work, omar is the name of a location off of the path, so the shell doesn't know where it is, or what to do with it if it found it.
```

omar@Megatron:/home$ cd omar

```yep that worked you are now in your home directory
```

omar@Megatron:~$ cd omar
bash: cd: omar: No such file or directory

```You're already in omar, so unless your home directory had a subfolder also named omar that's not a valid location
```

omar@Megatron:~$ cd /omar
bash: cd: /omar: No such file or directory

```Again /omar doesn't exist, you probably meant /home/omar
```

omar@Megatron:~$ cd /home
omar@Megatron:/home$ dir
omar
omar@Megatron:/home$ omar
bash: omar: command not found

```nothing new here
```

omar@Megatron:/home$ open omar
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console

```open is used for opening files to read them internally in programs, and really isn't all that useful from the shell, further more omar is directory, so even if open was useful it wouldn't know what to do with a directory
```

omar@Megatron:/home$ browse omar
bash: browse: command not found

```Just like it says there's no such thing as browse
```

omar@Megatron:/home$ cd omar
omar@Megatron:~$

```Yep and that worked and you're now back in your home directory back where you started this adventure.

---

### Post by Del Piero on 2008-01-04
Hey thanks for taking time to reply, i thought that when i am in Omar like the old versions it's gonna display something like that in the terminal:

> omar@Megatron:/home/omar$ 

But now when i type:
> 
omar@Megatron:~$ cd /home/omar


I get:
> 
omar@Megatron:~$

Can it be fixed to display which directory or sub directory i am in?

It's not working mate, as i said earlier:

> omar@Megatron:~$ cd /home/omar
omar@Megatron:~$ chmod a+x .conky_start.sh
chmod: cannot access `.conky_start.sh': No such file or directory

What do i do to browse the folder omar in the directory /home ???

Edit:

Never mind i am stupid, got it now. Pretty confusing though lol...thanks man....

---

