---
title: "Run many update commands from text file - how?"
date: 2015-01-21
forum: General Help
---

### Post by Stan_1936 on 2015-01-21
Hi,

I have the following set of update commands that I need to execute from the command line:

```

cd Downloads

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.7
sudo apt-get update

sudo apt-get install libglade2-0 python-glade2
sudo dpkg -i crossover_14.0.3-1.deb
sudo apt-get update

sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text
sudo apt-get update

sudo apt-get install libpkcs11-helper1
sudo apt-get install openvpn easy-rsa
sudo apt-get update

sudo apt-get install python-guestfs
sudo apt-get install libguestfs-tools
sudo apt-get update
sudo apt-get install ubuntu-virt virt-top virt-what
sudo apt-get update

sudo chmod 0644 /boot/vmlinuz*
sudo usermod -a -G kvm testguest
sudo chmod 0644 /boot/vmlinuz*
sudo apt-get update

```

I have saved this in a text file names "comdsequence.txt".

Now, I would like to use the Ubuntu command like to execute this file.

Questions:
1. How can I execute this file?
2. IMPORTANT: As you can see, I have included ```
sudo apt-get update
``` in a few places. Can I just use one ```
sudo apt-get update
``` at the very end (last line only)?

---

### Post by chait3 on 2015-01-21
Hi,

You will need a simple shell script to execute all these commands sequentially. 

1. Create a file "comdsequence.sh" or by any name. Paste your code that you want to run. Make the file executable using the following command:
    
> chmod +x comdsequence.sh

   Now you can run this file using the following command:

>  ./comdsequence.sh


2. You only need to do apt-get update once; that too after you have added the repository [after add-apt repository]

---

### Post by Dennis N on 2015-01-21
You would make your text file into a bash script by adding #!/bin/bash at the beginning of the file, then list the commands one per line:

```
#!/bin/bash
command1
command2
command3

```

Save the file with a name of your choice into ~/bin and then make it executable. Then open the terminal, type in the file name to start it and hope it works as you expect. 

A single apt-get install can install several packages with one command:
**sudo apt-get install package1 package2 package3**

BTW, I wouldn't mess with any files in /boot - hope you know what you are doing.

---

### Post by ajgreeny on 2015-01-21
I agree with Dennis N; do not mess with file permissions in /boot unless you really know what you're doing, and in view of your question here it looks as if you don't.  Sorry if that sounds rude!

Why do you want to use chmod to change the permissions of the vmlinuz files, which are 600 by default, not 644 as you want them?  Any actions you want to carry out on them will have to be done as root as they belong to root, so why make them readable by others?

---

### Post by Karlchen on 2015-01-21
Hello, Stan_1936.

About your question: 
> Can I just use one ```
sudo apt-get update
``` at the very end (last line only)?
_ Answer:_
```
sudo apt-get update
``` should be executed _before_ starting to download and install software packages.
"apt-get update" queries the software repositories and refreshes the local list of available software.
It should be easily understood that you want to know what is in the repositories _before_ you start installing anything.

Cheers,
Karl

---

### Post by Stan_1936 on 2015-01-21
Thanks for the help. I added this to the script file (and updated the original post here to reflect this):

```
sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text
sudo apt-get update
```

and then I executed the script file with:

```

sudo chmod u+x test.sh
./test.sh

```

It appears that the installation went as expected, however there were problems with both of the PPA sections:

```
Err http://ppa.launchpad.net /ubuntu/trusty i386 Packages
Err http://ppa.launchpad.net /ubuntu/main i386 Packages

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/trusty/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/dists//ubuntu/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/sublime-text-2/dists//ubuntu/trusty/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/webupd8team/sublime-text-2/dists//ubuntu/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download
```

For the 2 PPAs, I have followed the instructions here:
Wine: [https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)
Sublime Text Editor: [http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3](http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3)

Is there a problem with how I am adding the PPAs?

---

### Post by ian-weisser on 2015-01-21
Don't abuse 'sudo' in scripts. It may be better to run the entire script as sudo instead.

Don't run 'update' when you don't need to. You only need to refresh the package database after you add or remove a source, or of a long time has passed. You don't need to refresh the package database after a mere package install/remove.

Don't specify dependencies (libglade2-0, libpkcs11-helper1). Let the package manager figure it out. That's what it is for.

Do use a single list of the packages instead of one-at-a-time (separated by needless updates)

Do you REALLY need to add the PPAs? Can the version of Wine in the Ubuntu repos work? Remember that PPAs may introduce a file conflict or version conflict that breaks your upgrades in the future.

Example:
```
add-apt-repository ppa:ubuntu-wine/ppa
add-apt-repository ppa:webupd8team/sublime-text-2

apt-get update

apt-get install wine1.7 python-glade2 sublime-text openvpn easy-rsa python-guestfs libguestfs-tools ubuntu-virt virt-top virt-what

dpkg -i crossover_14.0.3-1.deb
```

---

### Post by Stan_1936 on 2015-01-21
> **ian-weisser said:**
> Do you REALLY need to add the PPAs? Can the version of Wine in the Ubuntu repos work? Remember that PPAs may introduce a file conflict or version conflict that breaks your upgrades in the future.

For both Wine and Sublime Text Editor, the PPAs were used to give the latest version. I would definitely need it for Wine; for Sublime-text, maybe not.

Do you also recommend that the following be placed at the beginning and end of your example?:
```

apt-get update
apt-get upgrade

```

I am currently using 14.04 Trusty. If these 2 lines were placed at the beginning and end, would that mean that the above 2 PPAs would cause trouble when upgrading to Ubuntu 14.10 and beyond?

---

### Post by ajgreeny on 2015-01-21
> **Stan_1936 said:**
> For both Wine and Sublime Text Editor, the PPAs were used to give the latest version. I would definitely need it for Wine; for Sublime-text, maybe not.

Do you also recommend that the following be placed at the beginning and end of your example?:
```

apt-get update
apt-get upgrade

```

I am currently using 14.04 Trusty. If these 2 lines were placed at the beginning and end, would that mean that the above 2 PPAs would cause trouble when upgrading to Ubuntu 14.10 and beyond?
Use the update and upgrade commands at the beginning only, there is no point in doing it a second time at the end unless you have added some new PPAs with the script, which might mean there are some newer versions of already installed packages available to you from those PPAs.

Any PPA repos should be disabled when you run an upgrade from one Ubuntu version to the next; I was under the impression that they were disabled automatically by the system, but never having upgraded that way (always a clean install for me) I may be wrong.

---

### Post by Stan_1936 on 2015-01-22
Thanks to all in this thread. All the replies were extremely useful.

> **ian-weisser said:**
> Don't abuse 'sudo' in scripts. It may be better to run the entire script as sudo instead.

Don't run 'update' when you don't need to. You only need to refresh the package database after you add or remove a source, or of a long time has passed. You don't need to refresh the package database after a mere package install/remove.

Don't specify dependencies (libglade2-0, libpkcs11-helper1). Let the package manager figure it out. That's what it is for.

Do use a single list of the packages instead of one-at-a-time (separated by needless updates)

Do you REALLY need to add the PPAs? Can the version of Wine in the Ubuntu repos work? Remember that PPAs may introduce a file conflict or version conflict that breaks your upgrades in the future.

Example:
```
add-apt-repository ppa:ubuntu-wine/ppa
add-apt-repository ppa:webupd8team/sublime-text-2

apt-get update

apt-get install wine1.7 python-glade2 sublime-text openvpn easy-rsa python-guestfs libguestfs-tools ubuntu-virt virt-top virt-what

dpkg -i crossover_14.0.3-1.deb
```

I ended up using your example unmodified and it worked as expected. This is a much better way to do it. Thanks.

---

