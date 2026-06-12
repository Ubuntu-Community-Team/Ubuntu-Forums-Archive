---
title: "help with batch/script"
date: 2012-10-19
forum: General Help
---

### Post by chadk5utc on 2012-10-19
Hello I know this isn't exactly linux but I need to search a lot of linux nodes as fast as possible for files. 
I do have a batch file that will read hosts.txt then login to each one via SSH within a private network
and calls another batch which I have for other things but need this one to search.
code below:
for /f %%i in (hosts.txt) do call :ACTIONS %%i
:ACTIONS
plink -ssh -pw passwd user@%1 -m search.bat

What I need this to do is search these machines for file1 file2 file3 file4 if the files "do not exist" on the remote
nodes Im trying to get a batch to get me the hostname and its ip and print this to a text file on my pc? so I can later 
resolve this. Any help would be greatly appreciated. I have googled for a few hours but still not finding what Im looking for.

Chad
ps hate windows/batch files

---

### Post by Habitual on 2012-10-20
file[1234] always the same files in the same locations? I guess no, else you wouldn't be searching for them.

Post search.bat
and Please!
[noparse]```
around scripts or script output
```[/noparse] tags 

Thank you,

---

### Post by Lars Noodén on 2012-10-20
> **chadk5utc said:**
> What I need this to do is search these machines for file1 file2 file3 file4 if the files "do not exist" on the remote
nodes Im trying to get a batch to get me the hostname and its ip and print this to a text file on my pc? so I can later 
resolve this. Any help would be greatly appreciated. I have googled for a few hours but still not finding what Im looking for.


If you have a [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html) formula that will locate the files for you, then you can call that from [ssh](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh.1.html).  ssh will then pass the exit code from find to your local script.


```

hostname=192.168.0.55;
if [ -z "$(ssh $hostname 'find */some/path/* \( 
  -name 'file1' -o -name 'file2' -o -name 'file3' \
  \) -print;' 2>&1 )" ];
then 
  echo $hostname >> /home/me/textfile.txt;
fi

```

[-z is a test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.htm) to see if the string returned  is of zero length, which it will be if none of the files are found.
>> means to append output to a file.

---

