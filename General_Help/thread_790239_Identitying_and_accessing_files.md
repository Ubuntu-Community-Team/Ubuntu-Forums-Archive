---
title: "Identitying and accessing files"
date: 2008-05-11
forum: General Help
---

### Post by thelugnut on 2008-05-11
I am  (still) having trouble understanding how to access files.

Here is my path:

[COLOR="DarkOrange"]/home/james/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/game[/COLOR]s

It is clearly seen that /home/james/bin is included.

I have a file in home/james/bin, named mary1.txt.

I issue the following command:

[COLOR="DarkOrange"]$ grep Mary mary1.txt[/COLOR]

I receive the following:

[COLOR="DarkOrange"]grep: mary1.txt: No such file or directory
[/COLOR]
I just don't get it.

Can somebody explain in clear simple terms so that this old brain might understand what I am doing wrong?

Thanks

---

### Post by Monicker on 2008-05-11
Your path is how the system knows where to look for executable file that you want to run.  Non executable files are NOT searched for in your path, you still have to specify the full path for them.

---

### Post by ryanhaigh on 2008-05-11
To do what you want (search for instances of the word Mary in mary.txt you woul use the following:
cat /home/james/bin/mary.txt | grep Mary

cat filename: basically prints the whole file to the screen (technically stdout)
| : this is a pipe, it 'pipes' the ouput of the cat command into the grep command
grep pattern: displays only those lines of the input that contain the pattern

As Monicker pointed out the path variable tells the system where to look for commands that you try to use. This is why you don't need to use /bin/grep the system looks for the grep command in those directories specified by your path variable, finds it it /bin and runs it.

If you add another directory to your path the system will look there but only for commands. The commands themselves expect a filename either relative (eg ../file for file in the parent directory, ./file or just file for file in the current directory) or absolute (eg /home/james/file) and won't look for the file in your path.

For example I created a empty file called thisisatest in /usr/bin. When I enter thisisatest at the commandline as a command the file is found in my path and the system tries to run it. However if I try to print the file using cat thisisatest the file is not found because it isn't in the current directory.

---

### Post by thelugnut on 2008-05-11
Well now, that helped me very much. I thank both of you for the replies.

Much obliged, for sure.
:guitar:

---

