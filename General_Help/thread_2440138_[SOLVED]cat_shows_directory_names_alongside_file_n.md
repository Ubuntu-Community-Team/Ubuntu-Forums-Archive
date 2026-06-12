---
title: "[SOLVED]cat shows directory names alongside file names"
date: 2020-04-06
forum: General Help
---

### Post by eminent2 on 2020-04-06
Hi,
When I want to see the content of a file using cat command after typing cat and pressing TAB key then the directory names appear beside the file name in the current path. Is it possible showing only file names when pressing TAB in this case? Logically, cat is only be able to work with files not directories.

---

### Post by owbizi on 2020-04-06
If I understood correctly, you want cat to only display the file names in the current path you are?

If so, I guess that would be up to cat + bash-completion: it shows both directory names and files because you might want to choose a file inside a directory in the current path.

---

### Post by eminent2 on 2020-04-06
> **owbizi said:**
> If I understood correctly, you want cat to only display the file names in the current path you are?
Exactly, How can I achieve this?

---

### Post by owbizi on 2020-04-06
My guess is that you would have to compile your own version of [cat]("https://github.com/coreutils/coreutils/blob/master/src/cat.c") and use that binary instead of the system provided.

As it is now, it is included in the [GNU coreutils]("https://github.com/coreutils/coreutils") among other tools commonly available as binaries from the get-go in Linux systems.

---

### Post by norobro on 2020-04-06
You can achieve what you want by modifying the bash-completion for the cat command.

Here's a bash function that does what you want:```
$ cat cat_no_dir

_cat_no_dirs ()
{
    COMPREPLY=()
    cur=($(compgen -o plusdirs -f -- "${COMP_WORDS[COMP_CWORD]}"))
    for ((i=0; i < ${#cur[@]}; i++)); do
        [ -d "${cur[$i]}" ] && continue
        COMPREPLY+=(${cur[$i]})   
    done
    return 0
}


complete -F _cat_no_dirs cat
```A test:
```
$ ls -lgG
-rw-r--r-- 1  377 Apr  6 18:19 cat_no_dir
drwxr-xr-x 2 4096 Apr  6 18:32 dir_1
drwxr-xr-x 2 4096 Apr  6 18:32 dir_2
drwxr-xr-x 2 4096 Apr  6 18:32 dir_3
-rw-r--r-- 1    0 Apr  6 18:32 file_1
-rw-r--r-- 1    0 Apr  6 18:32 file_2
-rw-r--r-- 1    0 Apr  6 18:32 file_3


$ source cat_no_dir


$ cat    # tab tab
cat_no_dir  file_1      file_2      file_3
```If you want this action to be permanent copy the file containing the function (cat_no_dir) to "/etc/bash_completion.d" and it will be sourced when you start a shell. For occasional use just source the file as I did here.

---

### Post by kneutron on 2020-04-07
Where's the LIKE button when you need it?? Nice solution @norobro :)

---

### Post by eminent2 on 2020-04-08
You are my champion !!! I love you &#55357;&#56856;&#55357;&#56856;&#55357;&#56856; Thank you very much bro &#55357;&#56856;&#55357;&#56856;&#55357;&#56856;&#55357;&#56856;

---

### Post by eminent2 on 2020-04-08
@norobro
Brilliant. I got it working.

---

### Post by CelticWarrior on 2020-04-08
> **kneutron said:**
> Where's the LIKE button when you need it?? Nice solution @norobro :)

There's "Solved" in the thread tools to indicate just that.

---

