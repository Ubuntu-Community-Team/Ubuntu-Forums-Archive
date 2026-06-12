---
title: "linux file structure question -- /opt directory, resolving commands"
date: 2014-10-19
forum: General Help
---

### Post by RangerK on 2014-10-19
I have two packages installed in my /opt directory: google chrome and sublime text.

From anywhere in the file structure, I can type "google-chrome" and launch it.  I can't do this with "sublime_text".

I thought the solution was either
1. to edit the $PATH variable to include the directories of the software I wanted.
2. install symbolic links of the executables in the /usr/local/bin directory

I assume the installation of google-chrome did this automatically, but that doesn't seem to be the case.

When I type:

> echo $PATH

I get only: 

> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

My questions:

1. How is the command "google-chrome" resolving to the google-chrome executable in the /opt/google/chrome directory?

2. What is the standard way to make "sublime_text" resolve to the sublime_text executable in the /opt/sublime_text directory?

Thanks!

EDIT:

> which google-chrome

resolves to

> /usr/bin/google-chrome

Does that mean I should copy the sublime_text executable to /usr/bin?  Should I copy just the one file?

---

### Post by yancek on 2014-10-19
The link below is to "unofficial documentation" for Sublimt_Text.  Did you create the symbolic link as shown on that page, to /usr/bin?

[http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html)

---

### Post by nerdtron on 2014-10-19
What is the output of  "ls -l /usr/bin/google-chrome"?

That is the command the launches chrome and we're not sure yet if it point to the chrome in /opt

You can also add additional directories to your $PATH. To do this you need to:
```

PATH=$PATH:/data/myscripts
export PATH

```

---

### Post by Impavidus on 2014-10-19
I don't have google chrome (nor sublime), but I assume it works the same as google earth, which I have installed. It automatically created a symbolic link in /usr/bin/ pointing to the executable in /opt/google/:```
$ which google-earth 
/usr/bin/google-earth
$ ls -l /usr/bin/google-earth 
lrwxrwxrwx 1 root root 34 okt  7  2013 /usr/bin/google-earth -> /opt/google/earth/free/googleearth
```But this link was created by the .deb package and will be removed when I uninstall the package. If you manually create the link, it's slightly better to put it in /usr/local/bin. It will be easier to find there if you uninstall the software.

---

### Post by bab1 on 2014-10-19
> **RangerK said:**
> I have two packages installed in my /opt directory: google chrome and sublime text.

From anywhere in the file structure, I can type "google-chrome" and launch it.  I can't do this with "sublime_text".

I thought the solution was either
1. to edit the $PATH variable to include the directories of the software I wanted.
2. install symbolic links of the executables in the /usr/local/bin directory

I assume the installation of google-chrome did this automatically, but that doesn't seem to be the case.

When I type:



I get only: 



My questions:

1. How is the command "google-chrome" resolving to the google-chrome executable in the /opt/google/chrome directory?

2. What is the standard way to make "sublime_text" resolve to the sublime_text executable in the /opt/sublime_text directory?

Thanks!

EDIT:



resolves to



Does that mean I should copy the sublime_text executable to /usr/bin?  Should I copy just the one file?
On my machine the executable is ```
/usr/bin/subl
```  From the terminal I can use ***subl *** to launch *sublime text2*.

---

### Post by RangerK on 2014-10-22
> **yancek said:**
> The link below is to "unofficial documentation" for Sublimt_Text.  Did you create the symbolic link as shown on that page, to /usr/bin?

[http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/getting_started/install.html)

Thank you, sir!

I figured it out, but for anyone else tuning in, here's the relevent part from the unoficial documentation:

Lastly, we create a symbolic link to use at the command line.

 
```
sudo ln -s /opt/Sublime\ Text\ 3/sublime_text /usr/bin/sublime
``` 

In Ubuntu, if you also want to add Sublime Text to the Unity luncher, read on. . . .


****************************************************************************************************

> **nerdtron said:**
> What is the output of  "ls -l /usr/bin/google-chrome"?

That is the command the launches chrome and we're not sure yet if it point to the chrome in /opt

You can also add additional directories to your $PATH.

Thank you.  The output is as follows:

lrwxrwxrwx 1 root root 31 &#1078;&#1086;&#1074; 19 23:18 /usr/bin/google-chrome -> /etc/alternatives/google-chrome

****************************************************************************************************

> **Impavidus said:**
> I don't have google chrome (nor sublime), but I  assume it works the same as google earth, which I have installed. It  automatically created a symbolic link in /usr/bin/ pointing to the  executable in /opt/google/

Thank you, Impavidus.  You're exactly right.  And in fact sublime-text did this as well.  Sublime text created a symbolic link named "subl" in /usr/bin.  I didn't realize this because in earlier versions it was "sublime-text".  :rolleyes:  :rolleyes:

Silly mistake.  Oh well.  At least I learned something.

****************************************************************************************************

> **bab1 said:**
> On my machine the executable is ```
/usr/bin/subl
```

Yup.  I think in earlier versions it was "sublime-text".  

It's like my grandma used to say: learning is painful.  :)

---

