---
title: "how to see commands used to start an application in 12.04"
date: 2013-01-02
forum: General Help
---

### Post by chrisc200 on 2013-01-02
How can I see the commands used to start an application?
e.g. I have a skype icon in unity bar, how do I see the commands used to start skype?

For my wine applications I found these under "applications" under the dash, then I could see the properties of the program, but where are all the other applications kept?

Thanks

---

### Post by vksingh on 2013-01-02
ps -ef|grep skype

note the process ID,
the go to /proc/<process ID>

cat stat
**6166 (a.out)**.......

In above, 6166 is process ID and a.out is name of my dummy application.

---

### Post by vksingh on 2013-01-02
Also, I will be interested to know how to get parameters passed to the executable.
For example, if i run the following:

./a.out hello

From /proc/<process ID>/stat , i get only **(a.out) **but not the argument [B]hello.

[/B]Please help.

Thanks,
Vivek

---

### Post by MG&amp;TL on 2013-01-02
While you can read that from /proc/<pid>/cmdline, you're probably better off reading its .desktop file in /usr/share/applications/

You want the Exec= line. :)

---

### Post by vksingh on 2013-01-02
I justtried[B]

./a.out ram[/B]

cat /proc/pid/cmdline
./a.outram 

there is no delimiter between executable and arguments. Its better showing in ps -ef|grep a.out 
**./a.out ram shyam**

Thanks,
vivek

---

### Post by MG&amp;TL on 2013-01-02
> **vksingh said:**
> 
there is no delimiter between executable and arguments.

For factual accuracy, they're delimited by the '\0' character, which doesn't display on terminals. Using:

```
cat /proc/<pid>/cmdline | tr '\000' ' '
```

...you can use spaces or any other character of your choice. But .desktop files or *ps* are the better way to go.

---

