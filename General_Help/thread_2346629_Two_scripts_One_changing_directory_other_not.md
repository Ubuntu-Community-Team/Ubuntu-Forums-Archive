---
title: "Two scripts: One changing directory other not?"
date: 2016-12-16
forum: General Help
---

### Post by Salil_Surendran on 2016-12-16
I have two scripts. One is :
```


    #!/bin/bash
    if [ $1 = 1 ]; then 
       dir=mydir-1.6_
    else
        dir=mydir
    fi
    cd ~/code/${dir}$2
    echo $(pwd)

```

The above script changes directories even though there are several posts that say that since a script is run in a sub-shell it should have no effect on the executing shell.


Now I have another script:


  ```
  #!/bin/bash
    dir=/WORK/temp/$1
    mkdir -p $dir
    cd $dir
    wget http://somurl.com/archive.zip
    unzip archive.zip

```

The above script unzips the file in the expected directory but leaves the calling shell in the same directory. What is the difference when cd is called in both scripts?

---

### Post by Impavidus on 2016-12-17
Does the first really put the calling shell in a new directory? The **echo $(pwd)** is running in the subshell, so that reports the new directory, but after the script terminates you should be back in your old shell and in your old directory.

If you don't run the stript as in **./script** or **bash script**, but instead source it as in **source script** or **. script**, then the script will execute in the current shell, which will change your current directory in the calling shell.

---

### Post by Salil_Surendran on 2016-12-18
> **Impavidus said:**
> Does the first really put the calling shell in a new directory? The **echo $(pwd)** is running in the subshell, so that reports the new directory, but after the script terminates you should be back in your old shell and in your old directory.

If you don't run the stript as in **./script** or **bash script**, but instead source it as in **source script** or **. script**, then the script will execute in the current shell, which will change your current directory in the calling shell.

Here is a demo

```
salilsurendran@salilsurendran-ThinkPad-P50:~$ myscript 1 4
/home/salilsurendran/code/mydir-1.6_4
salilsurendran@salilsurendran-ThinkPad-P50:~/code/mydir-1.6_4$ pwd
/home/salilsurendran/code/mydir-1.6_4
salilsurendran@salilsurendran-ThinkPad-P50:~/code/mydir$ myscript 2 3
/home/salilsurendran/code/mydir3
salilsurendran@salilsurendran-ThinkPad-P50:~/code/mydir3$ pwd
/home/salilsurendran/code/mydir3
salilsurendran@salilsurendran-ThinkPad-P50:~/code/mydir3$

```

---

