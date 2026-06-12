---
title: "What does command: &quot;sudo mkdir -p /data/{dta,mta}&quot; DO?"
date: 2014-07-16
forum: General Help
---

### Post by g35celicaz on 2014-07-16
Hello, 

I entered the following command: ```
sudo mkdir -p /data/{dta,mta}
``` and I get the following error: ```
Data /data/mta/fileblock.tch already exists, please remove it and try again
```

I know it makes a directory, but I am unaware as to where exactly it's located and what their names are

How can I solve this? 

Thanks for your help in advance!

---

### Post by varunendra on 2014-07-16
Any path starting from '/' means starting from root. So "/data/mta/fileblock.tch" means the directory "data" is in the root of the filesystem. I don't think this directory exists in root by default in any variant of Ubuntu, so it must have been created by you or some application you installed with root privilege.

To see the directory "data", open the file manager (by opening any folder/directory) and look for "filesystem". If you can't find it, simply press 'Ctrl-L' to edit the path in address-bar > type "/" > press 'Enter'. You should see the directory 'data' here. The directory "mta" should be within it.

---

### Post by Impavidus on 2014-07-16
The ting in curly braces is expanded by the shell before being given to the command as an argument. It is a comma separated list of the things that have to be put in place of the braces to be used in several arguments. In this case it expands to```
sudo mkdir -p /data/dta /data/mta
```So this command will use root permissions to create the directories /data/dta and /data/mta and, if it doesn't exist yet, first create /data.

---

### Post by g35celicaz on 2014-07-16
Great thank you, it worked!

I went inside my filesystem using gksudo nautlius and then deleted the data folder and then ran the command again using another application and it works now :popcorn:

---

### Post by at_first_light on 2014-07-16
Using {} is a method of shorthand called brace expansion. You can find more information about it here: [https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html) . Mkdir is a command line application for making directories. You can find more information about it here: [http://manpages.ubuntu.com/manpages/trusty/man1/mkdir.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/mkdir.1.html) . As mentioned by others the command in question will create directories dta and mta within a pre-existing folder called data that's located in your root directory. The reason you are getting an error is because there already is a folder called mta in the data folder, and therefore you can't make one. Since the mta folder already exists you would only need to create the dta folder. You can do so with the following command:

```

sudo mkdir /data/dta

```

---

