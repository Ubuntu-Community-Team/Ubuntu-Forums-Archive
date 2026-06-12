---
title: "Launcher: Application in Terminal"
date: 2007-11-07
forum: General Help
---

### Post by Stegga on 2007-11-07
Hi there,
I have installed XAMPP and wish to run the /opt/lampp/lampp start command from an icon.
I create the Launcher as Application in Terminal, and have the 'sudo /opt/lampp/lampp start' command and I have to type in the sudo password to run it.
I installed Thunderbird myself, as opposed to synaptic package manager installing it a few 'installations ago - last week! - and I had the same issue when I created the Thunderbird icon launcher, but if I install it Synaptec Package Manager, it has the same icon but with a 'thunderbird %u' as the command.
This makes me think that there is some 'path' type command (from windows days) that it is using, because there is no reference to the directory or folder that the tunderbird command is to be run from.
I also see that another of the application I run (Bluefish) has 'bluefish %F' in the command.

Please can someone give me some direction here.

Thanks,
Andrew

---

### Post by ohzopants on 2007-11-07
There is most definitely a PATH envrionment variable, you can find out what it is by typing
```
echo $PATH
```

When you install a package, usually a link to the executable is placed in a directory that is part of the path.  There are a lots of very good tutorials about modifying your path, so I won't regurgitate them here (I'm not that good at it anyway).

Are you running thuderbird with sudo?  That doesn't seem like a good idea.

---

### Post by Stegga on 2007-11-08
I was, but that was because if I didn't and my command was /opt/thunderbird/thunderbird start, it would say you don't have permission to do this!

---

### Post by ohzopants on 2007-11-08
I strongly recommend you make a link to the thunderbird binary to /usr/bin/ and make it executable as regular user.

---

### Post by Stegga on 2007-11-09
Could I trouble you to explain this concept to me:
I'm from a Windows background, and dispise the whole windows registry concept, but I'm struggling to understand the linux format.
Please tell me if I am correct or not below:
A binary is (like the executable, but it is) the entire 'application' in one 'file'.
If I 'install' a 'file' (as I am now trying to do with Sunbird), I download a .gz file.

I then type in tar -xvfz etc and it does something (extracts the files into a directory that I have chosen (lets say /opt/sunbird)). To run this, I then type at a terminal /opt/sunbird/sunbird start - or something liek that and it runs.

How do I do the path thing, what has /usr/bin got to do with things. I'm just struggling to get my head around this, so if you have the time, it would be greatly appreciated.

Andrew

---

### Post by ohzopants on 2007-11-09
Binaries and executables are pretty much synonyms.  It is not really the "entire application in one file", binaries can be self contained, but mostly they require extra files like libraries and can call other executables.

The .tar.gz file is a compressed file archive, just like a zip or a rar file; your extraction command will work, but you will probably have to use "sudo" since you probably don't have permission to write to the /opt/ directory.  I just downloaded sunbird, and it appears to be pre-compiled, so yes, you just need to call the executable to run the program.

The steps to install it are as follows:

```
tar xzvf sunbird-0.7.en-US.linux-i686.tar.gz
```

This will extract the program and all its files to a new directory called sunbird (the directory is already in the archive). You can do this in your home directory, so you don't need sudo and that's probably where you download files anyway.

```
sudo mv sunbird /opt/
```

This will move the sunbird directory to /opt/, you need to use sudo since you probably don't have write permissions to /opt/.

At this point you can run sunbird but you will have to use the full path, as follows:

```
/opt/sunbird/sunbird
```

Notice there is no "start" argument, that kind of argument is usually used for system services.

To be able to run sunbird without having to provide the full path to the executable you need to make a symbolic link to the executable in a directory that is part of your path:

```
sudo ln -s /opt/sunbird/sunbird /usr/bin/sunbird
```

A link (symbolic, or not) is the linux equivalent of a shortcut, except they are treated as if the file and the link are one and the same (although links can be deleted without deleting what they are linked to).

Now there is a link to sunbird in your path and you can run sunbird simply by typing "sunbird" at the command, or putting just "sunbird" in the application launcher.

You do not need to use sudo to run sunbird (that is a bad idea anyway).  Also of note is that you can install sunbird from the repositories using:

```
sudo apt-get install sunbird
```

The advantage to this is that it will be updated automatically, but the disadvantage is that sometimes the versions in the repositories are a bit behind what is available from the developper's website.

Sometimes when you download a program from a website you will have to compile it yourself, that is a whole different procedure.

Hope this helps.  If you have any other questions, don't hesitate; migrating from windows to linux can be tricky.  It's a change that is well worth it, however.

---

### Post by ohzopants on 2007-11-09
Sorry, I guess that previous post doesn't really explain the whole path thing.

The path is simply a list of directories that your system will search through for a filename when you provide a filename without a path.

For example, let's say I have an executable called "runme" in the directory "/dummy_directory/".

To run this file I have a number of choices:

1) Provide the full path to the executable:
```
/dummy_directory/runme
```

2) Go to the directory and run the file:
```
cd /dummy_directory
./runme
```

In this case notice that I had to use "./runme" that's because your current directory ( ./ ) is not part of the path.  That means that when you want to run a file that is in your current directory (and that directory is not in your path) you must explicitly tell the system to search in the current directory for the name of the file to run. This may seem strange, but you get used to it.

3) Add /dummy_directory/ to your path, then run the file:
```
export PATH=$PATH:/dummy_directory
runme
```

I don't really recommend this method.  First, if you start doing this your path will become huge and that may cause unexpected behaviour if you have 2 executables with the same name in two direcotries that are part of your path.  Secondly, the example I gave would only last for one session, you would have to redo it everytime you opened a console, you can make it permanent (but I'm not sure how).

---

### Post by Stegga on 2007-11-13
Thanks so much for this.
I haven't read it yet, but I will do so when I get home this evening!
Andrew

---

