---
title: "Create a function with zsh everytime the command is unknown"
date: 2015-02-24
forum: General Help
---

### Post by CkDGTAT on 2015-02-24
Hi,

The idea is to redirect the command to an editor to write a function in a file (e.g ~/.bash_functions ) when the command is unknown instead of executing it. I tried

```
if [[ -z $( echo $1 | grep unknown ) 
 then

echo "function $1(){" >> ~/.bash_functions                      
echo " " >> ~/.bash_functions
echo '}' >> ~/.bash_functions
sudo vim +":set syn=sh" +":normal G" +":start" +":normal k" ~/.bash_functions
source  ~/.bash_functions
$1

fi


```

---

