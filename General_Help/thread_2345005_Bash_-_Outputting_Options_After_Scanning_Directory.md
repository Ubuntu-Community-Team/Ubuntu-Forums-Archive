---
title: "Bash - Outputting Options After Scanning Directory"
date: 2016-11-29
forum: General Help
---

### Post by m-t-garcia1987 on 2016-11-29
I have a function that I have written which takes scanned files, and outputs them to an option menu for selection.

The only problem I have with this, is that whenever there is a file with a blank space in the name i.e. "name address.txt" it breaks it into two options 1)name, 2)address.txt.

Obviously selecting either causes a file not found error.

What can I do to mitigate this?

Side note: I have also tried:

```

 options=( $(ls -ap ~/ | grep -v / ) )


```

Just to see if it was related to the command I was using to get the file list in the first place but the results are the same.

```

function fivelines() {
  printf "Please select a file to display the last five lines of...\n\n";
  options=( $(find ~/ -maxdepth 1 -type f ) )
  echo;
  select opt in "${options[@]}" "Quit";
  do
    if [[ "$opt" != "Quit" ]]; then
      printf "You chose option $REPLY which is file $opt\n\n"
      export filename=$opt;
      break
    elif [[ "$opt" == "Quit" ]]; then
      exit
    fi
  done

```

---

### Post by steeldriver on 2016-11-29
If your file names don't contain newlines, then you should be able to use the builtin `mapfile` (or its synonym `readarray`) to construct the array e.g. given

```

$ ls -Ap
..afile  dir/  file  other dir/  other file  some dir/  some file

```

then

```

$ mapfile -t options < <(find -maxdepth 1 -type f)
$ 
$ printf '%s\n' "${options[@]}"
./other file
./file
./some file
./..afile

```

If you **do **have to deal with newlines in file names, then you can build the array using null separators like so:

```

$ options=()
$ while IFS= read -r -d '' f; do options+=("$f"); done < <(find -maxdepth 1 -type f -print0)
$ 
$ printf '%s\n' "${options[@]}"
./other file
./file
./some file
./..afile
./newline
file

```

unless you have bash > 4.4 in which case mapfile supposedly now supports a null delimiter directly.

FWIW, in zsh, there are qualifiers that let you do this kind of thing more directly using shell globs e.g. 

```

options=(*(D.))

```

---

### Post by m-t-garcia1987 on 2016-11-29
**Edit: For those that might come across this. This still, will not allow you to open a selected file if there is whitespace in the name. You would need to make modifications to the code in which you use to open said file. I did not include that here.**

I would like the ability to deal with newlines (I'm guessing whitespace is considered a newline in this case?).

So I took the line:

```

while IFS= read -r -d '' f; do options+=("$f"); done < <(find -maxdepth 1 -type f -print0)

```

and modified my code so that this is now what it looks like.

```

function fivelines() {
  printf "Please select a file to display the last five lines of...\n\n";
  while IFS= read -r -d '' f; do options+=("$f"); done < <(find ~/ -maxdepth 1 -type f -print0)
  echo;
  select opt in "${options[@]}" "Quit";
  do
    if [[ "$opt" != "Quit" ]]; then
      printf "You chose option $REPLY which is file $opt\n\n"
      export filename=$opt;
      break
    elif [[ "$opt" == "Quit" ]]; then
      exit
    fi
  done

```

This works fine. Thanks for your help.

---

