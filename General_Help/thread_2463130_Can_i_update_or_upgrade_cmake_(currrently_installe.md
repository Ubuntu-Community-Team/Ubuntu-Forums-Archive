---
title: "Can i update or upgrade cmake (currrently installed 3.14.0-rc2) in ubuntu 18,how?"
date: 2021-06-04
forum: General Help
---

### Post by priyanshu-gif on 2021-06-04
Hello Experts,
Can anyone please tell me that can i update and upgrade my cmake version to latest cmake version in ubuntu 18. if yes how can i do this .
since when i am installing ROOT in my machine then i am getting so many error related to cmake. so i just wanted to update it to a latest cmake version.
any type of help will be appreciated.
Thanks in advance1
Best Regards
Priyanshu

---

### Post by deadflowr on 2021-06-04
No idea where that is from since Ubuntu 18.04 only has 3.10.2-1ubuntu2.18.04.1 as the latest version.

---

### Post by monkeybrain20122 on 2021-06-04
Yes! Just download the precompiled binary (the .sh file) for Linux from [here]("https://cmake.org/download/"). Make it executable, run it to unpack cmake somewhere in your $HOME. Inside the cmake folder is a bin sub-folder where the binaries are. To use it, make simlinks for all contents of the bin sub-folder to your $PATH, easiest way to do it is to create a bin folder in your $HOME (/home/user_name/bin will be in your $PATH) 

```
mkdir bin
```

then do
```
ln -s /path/to/cmake/folder/bin/* /home/user_name/bin
```

Then you can invoke cmake and ccmake just by typing "cmake" or "ccmake" in the terminal like you usually do.

You can check by typing in the terminal (it requires a reboot or logging out and logging in if you just create /home/user_name/bin and it didn't exist before)
```

which cmake
cmake -version
```

and

```
which ccmake

ccmake -version
```

No need to instal, no sudo required. If you want to remove it, just delete the cmake folder and the symlinks in /home/user_name/bin

---

### Post by priyanshu-gif on 2021-06-04
Okay, thank you very much for your reply.
actually before this , i installed cmake by using the source distribution not using the binary distribution. and using that installed cmake i installed a software Geant4 then now i want to know that if  i change my cmake version then will it affect running the Geant4 because Geant4 also installed by using some functions of cmake. 

or if i change cmake version then will i have to again build and install the Geant4 ?
and yes, again i don't want to install its binary distribution, i want to install its source distribution so will it affect my software Geant4 ?

also one more thing, i just wanted to know that can i update my cmake version without uninstalling the previous one, just previous one should update again. is it possible ?
can you please help me with this to understand this doubt so i can update it without any fear since to install the software like Geant4  is difficult task that's why i don't want to disturb it.
Thanks
Regards
Priyanshu

---

### Post by monkeybrain20122 on 2021-06-04
You can do the same if you compile from source (though I don't see why that is necessary), install cmake in your home and make symlinks and use as above then you are done. No need to mess with system files or use root privilege. $HOME/bin takes precedent over /usr/bin so whichever version in $HOME/bin would be your default. You can then  run your Geant4 and see if it is affected by the change without changing anything in system files

Again if it is not what you want just delete the cmake folder and remove the symlinks in $HOME/bin then you revert to the version in /usr/bin. I don't think how you compiled Geant4 will have anything to do with upgrading cmake. cmake is just a compile tool, it doesn't contain libraries that the program has to load at run time.

---

