---
title: "What is a package, really?"
date: 2019-04-14
forum: General Help
---

### Post by John_Patrick_Mason on 2019-04-14
A quick Google search reveals that packages are a collection of items: scripts, libraries, text files, a manifest, a license, etc... I know what scripts and text files are, and I also have a general idea about what a license is, but what about libraries and a manifest? Could somebody explain what these are exactly?

Also, when I decide to install a package, say mpg123 like so,

```
sudo apt install mpg123
```

and use the utility like so,

```
mpg123 ~/Music/"Mozart - Requiem.mp3"
```

what is the name of the package?

What about if I do:

```
sudo apt install tofrodos
```

and then:

```
todos test_file.txt
```

What is the package name here? Is it tofrodos or is it todos/fromdos? Do package names have to have the same name as the utility contained within the package? This is what confuses me when people talk about packages. In Windows, the term "package" isn't used. When you want to install a program, you download the executable, preferably from a trusted source, and then double-click on the executable file to install it. The name of the executable is the same name as the application once installed.

---

### Post by CatKiller on 2019-04-14
There is absolutely no reason, other than convenience, for the name of the package to have any relation at all to the names of any of the files inside it, nor to the name of the .deb file that's actually downloaded.

The [package file](https://en.wikipedia.org/wiki/Deb_(file_format)) contains an archive of the files that will be installed, to locations fitting the [Filesystem Hierarchy Standard](https://en.m.wikipedia.org/wiki/Filesystem_Hierarchy_Standard), and a list of *other* packages that are required for the software to function.

There is no Windows equivalent to packages and, in general, you should not attempt to think of Ubuntu in Windows terms. They are not the same, and you will only cause yourself confusion by thinking that they are.

---

### Post by 1clue on 2019-04-14
> **John_Patrick_Mason said:**
> A quick Google search reveals that packages are a collection of items: scripts, libraries, text files, a manifest, a license, etc... I know what scripts and text files are, and I also have a general idea about what a license is, but what about libraries and a manifest? Could somebody explain what these are exactly?


[LIST]
[*]script -- A human-readable text file which is intended to be executed by the computer. It requires an interpreter of some sort which can understand the language(s) contained in the file.
[*]library -- A file containing compiled bytecode which is directly executable by the CPU on the system. Alternately it could be bytecode intended for a virtual machine. Not readable by a human.
[*]text file -- Self explanatory I think.
[*]manifest -- When you order a package from Amazon and it has 6 things in it, you get a piece of paper either inside the box or taped to the outside. This is a manifest. The package manifest is the same idea but more specific and detailed.
[*]license -- Not going to preach, but you should figure this one out. Open Source licenses tend to be very readable by people who are not lawyers. And they're important.
[/LIST]

> 
Also, when I decide to install a package, say mpg123 like so,

```
sudo apt install mpg123
```

and use the utility like so,

```
mpg123 ~/Music/"Mozart - Requiem.mp3"
```

what is the name of the package?

What about if I do:

```
sudo apt install tofrodos
```

and then:
  
```
todos test_file.txt
```

What is the package name here? Is it tofrodos or is it todos/fromdos? Do package names have to have the same name as the utility contained within the package? This is what confuses me when people talk about packages. In Windows, the term "package" isn't used. When you want to install a program, you download the executable, preferably from a trusted source, and then double-click on the executable file to install it. The name of the executable is the same name as the application once installed.

Catkiller already pretty much covered all of this. But package names in a distribution are not random.

You could define a package and put stuff in it, it's kind of like a zip file. Your package could have all of the features of an Ubuntu .deb file (package). You can name it spongebob.deb and it will have some random stuff in it, none of which have anything to do with an irritating children's cartoon.

When a Linux distribution is made, its maintainers usually use "upstream" project names as their package names. Otherwise, for packages maintained by the distro, they will try to make a name which is informative to the user base. Sometimes there is a customary form for the package name. For example, a package containing libraries is almost always named '**lib**something'. Packages relating to QEMU usually are named '**qemu**something'. Variants of the system logger tend to contain 'syslog' in the name.

---

### Post by 1clue on 2019-04-14
To reverse some of this, if you want to find out what package installs a file, you can do this:

```
dpkg -S /path/to/file
```

For example, 

```

$ dpkg -S /bin/ls
coreutils: /bin/ls

```

---

### Post by John_Patrick_Mason on 2019-04-14
[QUOTE=CatKiller]The [package file]("https://en.wikipedia.org/wiki/Deb_(file_format)") contains an archive of the files that will be installed, to locations fitting the [Filesystem Hierarchy Standard]("https://en.m.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), and a list of *other* packages that are required for the software to function.[/QUOTE] Also known as dependencies, correct?

Also, before installing a package, do I need to run:

```
sudo apt update
```

formerly known as sudo apt-get update, every time? What about running:

```
sudo apt upgrade
```

formerly known as sudo apt-get upgrade? Back when I was learning the terminal using William E. Shotts' *The Linux Command Line*, when the book introduced the concept of package management, it suggested typing:

```
sudo apt-get update; sudo apt-get upgrade
``` but I was always afraid of typing in the second part of that command, because I didn't want to upgrade my Ubuntu version to a more recent version.

Also, does running the Ubuntu Software Updater update all the utilities/applications installed through the terminal, or do I need to run sudo apt update/upgrade every time before installing a utility/application through the terminal?

Edit: Just noticed that two other people posted before this post.

---

### Post by 1clue on 2019-04-14
**sudo apt update** pulls the list of current packages from the servers registered in your configuration.

**sudo apt upgrade** checks your installed packages and compares the versions installed with the latest greatest, and then installs whatever is necessary.  This is an over-simplification but suitable for the discussion.

You don't need to **sudo apt update** but if you don't you risk installing an older package which will then be upgraded next time you do an upgrade, so you will have installed it twice.

You don't need to **sudo apt upgrade** before installing your new package, but depending on the flags you use the same situation might come up and you will wind up installing things more times than necessary.

To combine the two above commands, you would:

```
sudo apt update **&&** sudo apt upgrade
```

The **&&** will only execute the second command if the first one ran without errors.

Apt will only upgrade in the same "branch."  The command **do-release-upgrade** will upgrade you from one 'release number' of Ubuntu to the next. For example, if you're on Ubuntu 16.10 you could do **do-release-upgrade** to get to 18.10.

---

### Post by John_Patrick_Mason on 2019-04-15
First of all, thank you all for taking the time to answer my questions. I really appreciate it. I did end up reading *The Linux Command Line* cover to cover, but because I learned the command line so quickly, I still do have some gaps in my knowledge.

[QUOTE=1clue]When a Linux distribution is made, its maintainers usually use "upstream" project names as their package names.[/QUOTE]

In this case, Debian, correct? Downstream would be Linux Mint.

[QUOTE=1clue]**sudo apt update** pulls the list of current packages from the servers registered in your configuration.[/QUOTE]

And this is important because package names sometimes change, as in the case of dos2unix to tofrodos, right?

[QUOTE=1clue]You don't need to **sudo apt update** but if you don't you risk  installing an older package which will then be upgraded next time you do  an upgrade, so you will have installed it twice.[/QUOTE]

If you forget to run **sudo apt update** before installing a package and you decide to run **sudo apt upgrade** after it gets installed, will **sudo apt upgrade** delete the path to the utility, or will your system show two versions of different utilities installed on your system, like on some servers, i.e. dos2unix/unix2dos and todos/fromdos both pointing to different locations, when using them with the **which** command?

---

### Post by CatKiller on 2019-04-15
> **John_Patrick_Mason said:**
> And this is important because package names sometimes change, as in the case of dos2unix to tofrodos, right?
No, simply to see if there's a newer version.

> If you forget to run **sudo apt update** before installing a package and you decide to run **sudo apt upgrade** after it gets installed, will **sudo apt upgrade** delete the path to the utility, or will your system show two versions of different utilities installed on your system, like on some servers, i.e. dos2unix/unix2dos and todos/fromdos both pointing to different locations, when using them with the **which** command?
No, nothing like that.

For each package that you have installed where the version number of the package from the repository is higher than the version that you've already got, apt upgrade will download and install the new version. apt update simply refreshes the list of which versions are available from each repository.

There are two situations where apt update is important: where you've added or removed a repository; and where a package has been updated twice since the last time you did an upgrade, but your local list of available packages refers to the intermediate one which is no longer available. It's simply a good habit to get into to always run update before you do any package management.

You should stop trying to think of it in the abstract. Simply install Synaptic and install and uninstall some stuff. It shows what's happening quite well.

---

### Post by 1clue on 2019-04-15
> **John_Patrick_Mason said:**
> First of all, thank you all for taking the time to answer my questions. I really appreciate it. I did end up reading *The Linux Command Line* cover to cover, but because I learned the command line so quickly, I still do have some gaps in my knowledge.


No problem, but reading a book like that without taking the time to use everything in it is kind of pointless. You will certainly miss a lot of information without the practice and experimentation.

> 
In this case, Debian, correct? Downstream would be Linux Mint.


No. **Upstream** means the place the package came from. It's true that Ubuntu is "based on" Debian, but that doesn't in any way mean that everything in Debian is newer than everything in Ubuntu.

Creating a new distribution from scratch is a ton of work. Some distros do it anyway, and come up with something "original" so to speak. But probably most new distros start with what some other distro did. Ubuntu started with Debian. This means they used Debian's package manager and some other tools debian writes, and the same basic approach toward doing things. 

However some packages in Ubuntu are newer than the equivalent package in Debian.

A distribution is a collection of software packages. Each package has a group of maintainers (developers) who focus on development of that one package. For example, the Linux kernel is a package. The init system is a package, there are several to choose from but in most cases the distribution will decide that for you. Likewise a logger is a package, and there are several to choose from there too. 

If you open a command line and type **dpkg -l** you will see a list of packages your system knows about. Each one of these represents a team of software developers who maintain a product. Each product has an official website and each project is its own **upstream**. 

A distribution is comprised of, among other things, this list of software packages. The maintainers will download the source, compile it, and build a binary package with all the files necessary for their default configuration. There's way more to it than that, but it's the basic idea. There is also testing, bug patches, and a lot of other things.

Canonical, the company which maintains Ubuntu and its official variants, makes its own decisions about whether an **upstream** project is ready for their stable branch. They don't follow Debian's lead here. They make their own decisions about which packages to include in the distribution. 

Keep in mind that if the people who started Ubuntu thought there was nothing wrong with Debian, they would be using Debian. Also keep in mind that all these distributions are pulling from the same upstream sources. So the reason for the dissatisfaction would be in the priorities and/or the compilation or configuration options provided by the maintainers of the existing distribution.

> 
And this is important because package names sometimes change, as in the case of dos2unix to tofrodos, right?



If you forget to run **sudo apt update** before installing a package and you decide to run **sudo apt upgrade** after it gets installed, will **sudo apt upgrade** delete the path to the utility, or will your system show two versions of different utilities installed on your system, like on some servers, i.e. dos2unix/unix2dos and todos/fromdos both pointing to different locations, when using them with the **which** command?

Catkiller's answer to this is as good as I could give you.

---

### Post by John_Patrick_Mason on 2019-04-16
[QUOTE=1clue]No problem, but reading a book like that without taking the time to use  everything in it is kind of pointless. You will certainly miss a lot of  information without the practice and experimentation.[/QUOTE]

But I did, to the point where I was starting to develop RSI in my hands, where I had to get an ergonomic keyboard. It's just that the chapter devoted to package management doesn't really explain what a package is. All what it says is, "Here are the tools for package management, have fun." It's a good book, but there are other chapters like that, such as the one on networking.

Upstream would be like coreutils from the GNU project, or the GNOME desktop environment, right?

Do these people get compensated, like Bram Moolenaar et al. for the vim project, or does Ubuntu, Debian, and the other distributions, just take packages from them and contribute nothing in return? I'm asking because I've read comments from people about how Ubuntu contributes very little "upstream." I don't know if that's a fair criticism or not.

---

### Post by 1clue on 2019-04-16
> **John_Patrick_Mason said:**
> But I did, to the point where I was starting to develop RSI in my hands, where I had to get an ergonomic keyboard. It's just that the chapter devoted to package management doesn't really explain what a package is. All what it says is, "Here are the tools for package management, have fun." It's a good book, but there are other chapters like that, such as the one on networking.


LOL. A package is a compressed file with a strict structure and specific additions to enable a program to put everything in the correct places with the correct permissions.

> 
Upstream would be like coreutils from the GNU project, or the GNOME desktop environment, right?


Upstream would be the team that develops coreutils or gnome desktop. But yes, that's the idea.

> 
Do these people get compensated, like Bram Moolenaar et al. for the vim project, or does Ubuntu, Debian, and the other distributions, just take packages from them and contribute nothing in return? I'm asking because I've read comments from people about how Ubuntu contributes very little "upstream." I don't know if that's a fair criticism or not.

Technically neither answer is true. There is no rule about compensation, but every distribution sponsors open source projects as far as I know. 

But that's a very simple answer that has not much to do with reality either.

--

The premise of Open Source is that everyone contributes something back. You get free use of what's out there, and eventually you do something for the community in return. It doesn't have to be code. It could be money, or documentation, or being a really good forum user who helps new people figure it all out. It could be making a bunch of window manager themes and posting them online. It could be hosting a forum on a site you pay for.

Nobody worries about whether people contribute back right away. It may take decades for a user to find a good project or be in a position where contributing back is even possible. The only unforgivable sin is to break the terms of the licenses in question, especially in order to claim the work as yours for profit.

--

Many (most?) Open Source projects are planned, programmed and published without direct monetary compensation for the people doing the work. The projects may accept donations if someone chooses to do so, or perhaps somebody is willing to pay for a feature to be added to the project and the team accepts the pay.

Many open source projects come from a government.

Also many Open Source projects are managed by commercial for-profit companies. The programmers likely get whatever pay they get normally, and the company releases at least one copy of the code under an Open Source license. So in those cases "upstream" is paid work by professional programmers making their normal salary. The software in question may be released under more than one license. Sometimes the free part is a usable subset of a larger commercial project.  Examples are:
[LIST=1]
[*]Wine is a subset of Crossover Office.
[*]VMware has free components which are used within their commercial offerings
[*]There are many more.
[/LIST]

One common model in the past was that some package (let's say 'perl') is written for free, and the author writes a book documenting how to use perl. He sells the book, and makes his money. The book is full of useful information you're unlikely to find elsewhere, such as a bunch of Larry Wall's twisted humor -- which is worth the price of the book by itself -- and details of features that most people don't write about in blogs or questions to forums.

Another common practice is that a corporation will hire the author of a project to use/install/configure that project on their site to their specifications. Often this will involve additional coding which is often licensed by the programmer within the project as a new feature.

--

Getting back to distributions contributing back, this happens in many ways. Many of these things is invisible to the user. 
[LIST]
[*]Distributions like Ubuntu do a lot of testing, and in that process they will find bugs and post a bug report back, often with a patch to fix the problem.
[*]They write their own software, some of which is open source. This constitutes contributing back exactly as it was originally envisioned.
[*]They get new users involved in Open Source, which provides interest in the projects being used.
[*]Sometimes they contribute money to a project as I mentioned above.
[/LIST]

In some ways a distribution is a consumer of Open Source, and in other ways it's a provider. Mostly I think of it as a proxy. 

[LIST]
[*]Canonical is a for-profit company that built *buntu as a stable platform on which they could provide their for-profit applications and services. In this way Canonical is a consumer of Open Source.
[*]Canonical provides testing, documentation, new code and bug fixes. In this way Canonical is a provider of Open Source.
[*]Canonical provides its users with a collection of Open Source. Those users are consumers of Open Source. This makes Canonical a proxy for Open Source.
[/LIST]

---

### Post by John_Patrick_Mason on 2019-04-18
I still find it weird to think of the Linux kernel as a "package." I  thought packages only contained utilities like grep or applications like  the Vivaldi browser, or maybe packages that are specially designed to  enable other packages to function, i.e. dependencies.

What are  some of the major upstream projects that Canonical has decided to  incorporate into Ubuntu? I now know there's the GNU project, which gave  coreutils and GNOME 3. I'm assuming there's also the Linux kernel  itself. Are there any others? Major ones, I mean.

And why is  Ubuntu called a distribution as opposed to an operating system? You  wrote that a distribution is just a collection of software packages,  but is it really that simple? As a native English speaker, when I think  of the word "distribution" in the context of computing, I think of  somebody's take on something, or  in this case, Ubuntu is Canonical's take on what a Linux-based  operating  system should look like.

Also, just a quick refresher, but compiling  just means translating source code written in a language like BASH or  Python into machine code AKA binary, right?

---

### Post by 1clue on 2019-04-18
Open a terminal and type **dpkg -l**. Each of those things is a package.

You seem to be confusing licenses with packages and projects. Gnome Foundation controls gnome, and they seem to be pretty tight with RedHat. Seeing as their site is hosted by RedHat, I would strongly suspect that Gnome Foundation is one of RedHat's projects. The license may be GPL but that does not in any way mean that GNU project drives the decisions.

While I would like it to be different, the Open Source community is highly political. Many distributions choose software packages based on their political relationships with various projects rather than some judgement of suitability. You might want to start reading about that if you really want to get confused.

The operating system is the Linux Kernel. Everything which is not the kernel is an application or documentation. People use terms like 'tool' or 'service' or whatever else to categorize the applications but as far as the kernel is concerned there are only applications with various capabilities.

Ubuntu is a collection of software maintained by a commercial company, who distributes that software to interested parties without charge. That makes them a distribution. Ubuntu is Canonical's take on what a desktop should look like, or a server, depending on what you installed.

Compiling:
Bash and python are interpreted languages, so no.

Any time you have a human-readable language (c, bash, python, Java, fortran, c++, Forth, Ada, ad nausea infinitum) the computer processor can't directly understand that language. It needs to be processed in a way that the CPU can figure out what to do.

A compiler translates source code one time, on one computer, and creates a binary file or files. This binary file set can be executed many times without recompiling, and it can also be copied to other similar systems and executed there many times.

An interpreter reads the source file directly, and converts the program into executable code every time you use it. Some languages translate the source file(s) once per run, and others can generate code on-the-fly and execute it, so there is always some sort of interpretation going on. But the key here is that if you are using an interpreted language, the interpreter must be on the system which runs the program, and must be used while you are running the program.

To make it more interesting, some languages compile into an intermediate transportable byte code. This is no longer human readable, but not executable by the cpu directly either. Microsoft Office is built on this scheme, you need to have a library on your system which understands their byte code.

One variant of this is Java. There are hundreds of computer languages which compile into Java Virtual Machine byte code, and for many years Java compiled apps were no different from this intermediate transportable byte code I talked about in the previous paragraph. But there are a few differences:
[LIST=1]
[*]Java is a virtual machine.
[LIST=1]
[*]That means that -- according to the original theory -- nothing running inside of the VM can touch anything running outside of it.
[*]That rule didn't last long, because everyone wanted to "do work" on things outside of the VM.
[*]All sorts of exceptions and mechanisms were made to do that work, and so here come the security problems.
[*]There are other issues with Java, but interaction with the "outside world" multiplied them.
[/LIST]

[*]There is a Java chip. You can actually get a hardware CPU on a board which executes Java byte code natively. So in that case Java is a pure compiler, but only when the byte code is executed on a Java chip.
[/LIST]

At any rate, whether complied into intermediate byte code or compiled for a virtual machine with a foreign instruction set, either of these things requires additional software on the system which wants to run it, during runtime.

---

### Post by oldrocker99 on 2019-04-18
A quick answer to them OP's question is that packages in Linux are like the Windows .exe files that install a program.

---

### Post by CatKiller on 2019-04-18
> **John_Patrick_Mason said:**
> I still find it weird to think of the Linux kernel as a "package."

It isn't. A package may *contain* the Linux kernel, however.

>  I  thought packages only contained utilities like grep or applications like  the Vivaldi browser, or maybe packages that are specially designed to  enable other packages to function, i.e. dependencies.

Anything can be installed as a package. It's just a tidy way to bundle files up together. You can have packages of source code for the user to compile themselves, if you want. Or packages of images. Or packages of documentation. Or packages of just header files. All sorts.

> And why is  Ubuntu called a distribution as opposed to an operating system? You  wrote that a distribution is just a collection of software packages,  but is it really that simple? 

Yes, it's really that simple. Collect up a bunch of software that you think might be nice together, give it a default configuration, and you've created a distribution. The definitive line as to what, exactly, determines the necessary requirements for an operating system is fuzzy, but collections of software distributed together are definitely distributions.

Just the kernel wouldn't be an operating system. Just the kernel and GRUB wouldn't be an operating system. Just the kernel, GRUB and systemd is getting there, but still wouldn't be able to do much. As you start adding more bits, somewhere you will pass a point where you could say, "yes, that is definitely an operating system," but where, exactly, that point is depends on interpretation. So no one bothers. Distributions are distributions: job done.

---

### Post by 1clue on 2019-04-18
> **CatKiller said:**
> It isn't. A package may *contain* the Linux kernel, however.


Strictly true, but in practice the line blurs.

> 
Anything can be installed as a package. It's just a tidy way to bundle files up together. You can have packages of source code for the user to compile themselves, if you want. Or packages of images. Or packages of documentation. Or packages of just header files. All sorts.


Traditionally you would have a binary package which contains documentation as well, and a source package for those who want that. Which may also contain the same documentation. Sometimes headers are separate from libraries but not usually.

> 
Yes, it's really that simple. Collect up a bunch of software that you think might be nice together, give it a default configuration, and you've created a distribution. The definitive line as to what, exactly, determines the necessary requirements for an operating system is fuzzy, but collections of software distributed together are definitely distributions.


Yes and no, what you're describing is not actually very simple at all. You're collecting a bunch of source tarballs, configuring, compiling, tweaking for your distribution, adding documentation and putting all that into a package. Not to mention all the decisions as to what goes into the distribution and what doesn't, and testing, and bug reports, and distro-specific development.

An operating system is the interface between hardware and the user space applications. So yes, the Linux kernel is the operating system. Even components which are traditionally part of the operating system, once separated out into user-space code, are no longer part of the operating system. These pieces may be necessary to run the kernel in any useful way, but they're user-space.

> 
Just the kernel wouldn't be an operating system. Just the kernel and GRUB wouldn't be an operating system. Just the kernel, GRUB and systemd is getting there, but still wouldn't be able to do much. As you start adding more bits, somewhere you will pass a point where you could say, "yes, that is definitely an operating system," but where, exactly, that point is depends on interpretation. So no one bothers. Distributions are distributions: job done.

The kernel can run without an init manager. You would be single-threaded and single application, but you can boot it.

Try out Arch or Gentoo. There is a very small bit of code necessary to actually run on the system.

---

### Post by again? on 2019-04-18
If you want to understand deb packaging better, have a look at this easy to follow tutorial 
to create your own simple deb package.
[How-To: Create a Debian package and a Debian repository]("https://blog.heckel.xyz/2015/10/18/how-to-create-debian-package-and-debian-repository/")

---

### Post by CatKiller on 2019-04-18
> **1clue said:**
> Strictly true, but in practice the line blurs.

I think the OP had conflated packages with things like snaps or flatpaks. It's an important distinction that although the kernel may be distributed as one of squillions of packages, that doesn't really have much to do with how it works once it's installed.

> Traditionally you would have a binary package which contains documentation as well, and a source package for those who want that. Which may also contain the same documentation. Sometimes headers are separate from libraries but not usually.

There are a bunch of -doc or -dev packages in the repositories. If you don't need the documentation, or you don't need the headers, you don't need those packages. Again, to show that packages are just a means to distribute and install files.

> Yes and no, what you're describing is not actually very simple at all. You're collecting a bunch of source tarballs, configuring, compiling, tweaking for your distribution, adding documentation and putting all that into a package. Not to mention all the decisions as to what goes into the distribution and what doesn't, and testing, and bug reports, and distro-specific development.

I never said it was *easy*. But the idea is simple.

> An operating system is the interface between hardware and the user space applications. So yes, the Linux kernel is the operating system. Even components which are traditionally part of the operating system, once separated out into user-space code, are no longer part of the operating system. These pieces may be necessary to run the kernel in any useful way, but they're user-space.

The kernel can run without an init manager. You would be single-threaded and single application, but you can boot it.

Like I said: fuzzy. Some people would class something that booted an ran one application an operating system. Others might say that it should be able to run applications of the user's choosing. Far simpler to not bother to get into the weeds and simply call a distributed collection of software a distribution. Which was my point. And I certainly wouldn't class a kernel with no userland as an operating system.

---

### Post by John_Patrick_Mason on 2019-04-21
[QUOTE=1clue]Seeing as their site is hosted by RedHat, I would strongly  suspect that Gnome Foundation is one of RedHat's projects. The license may be GPL but that does not in any way mean that GNU project drives the decisions.[/QUOTE]

Suspect? You mean nobody knows for sure? All this time I thought the GNU project was an independent project with close links to Richard Stallman that got a significant amount of its money through the Free Software Foundation, which *is* headed by Richard Stallman. 

[QUOTE=1clue]Ubuntu is a collection of software maintained by a commercial company,  who distributes that software to interested parties without charge. That  makes them a distribution.[/QUOTE]

Or, to put it in other words, Ubuntu and its variants are called "distributions" because Canonical simply *distributes* the software, not necessarily their own, to other people, right?

I'm  glad you touched upon bytecode, because that was going to be my next  question. At first, I assumed you meant binary/machine code 1's and 0's.  Correct me if I'm wrong, but bytecode is not directly executable by the  CPU, but it is executable by a virtual machine, which mimics a real  CPU. If so, then what did you mean when you said that a library is a  file containing compiled bytecode? Do you mean to say that the file *is* in bytecode? Or did you mean to say that the file *was* in bytecode, but has since been compiled into binary/machine language 1's and 0's, and is hence in binary?

Also, what is this binary package that you keep referring to? Why the adjective? Why not just call it a package?

---

### Post by 1clue on 2019-04-21
> **John_Patrick_Mason said:**
> Suspect? You mean nobody knows for sure? All this time I thought the GNU project was an independent project with close links to Richard Stallman that got a significant amount of its money through the Free Software Foundation, which *is* headed by Richard Stallman. 


[https://www.gnome.org/foundation/](https://www.gnome.org/foundation/)

The first clue about who gives how much, is if they have a "supporting organizations" section and especially if they have variable sizes in logos. A bigger logo means more money, but usually they sort the companies in the group alphabetically.

The FSF is in there, but so are some companies with deeper pockets.

***Edit:** I personally don't follow gnome news. I don't particularly care for it, and I certainly don't like its decision to hard-link to systemd for too many reasons to list. That's why I said 'suspect.' There are countless things which are much more important to me than following RMS politics or gnome/systemd/redhat projects.*

> 
Or, to put it in other words, Ubuntu and its variants are called "distributions" because Canonical simply *distributes* the software, not necessarily their own, to other people, right?


Yes.

> 
I'm  glad you touched upon bytecode, because that was going to be my next  question. At first, I assumed you meant binary/machine code 1's and 0's.  Correct me if I'm wrong, but bytecode is not directly executable by the  CPU, but it is executable by a virtual machine, which mimics a real  CPU. If so, then what did you mean when you said that a library is a  file containing compiled bytecode? Do you mean to say that the file *is* in bytecode? Or did you mean to say that the file *was* in bytecode, but has since been compiled into binary/machine language 1's and 0's, and is hence in binary?


In the case where I used it, I was talking about any sort of "executable" not readable by humans. Traditionally, a "library" in Linux is binary content directly executable by the CPU, the way 'c' is compiled.

In my personal opinion, there are too many types of "byte code" categories in the traditional sense, the way you said it. Executable by a VM, executable by a "runtime library", executable by Microsoft Word, a foreign processor's binary executable (java), whatever. There are probably dozens of strategies to partially compile software that have been used over the history of computing, and most of them are probably still around. In a discussion like this one, there are probably three reasonable classes: 
[LIST=1]
[*]Source code (Stored exactly as the programmer typed it, whether executable by an intepreter or waiting to be compiled) 
[*]Binary executable (compile once, distribute to multiple computers, executable directly by the CPU of the system the library resides on. 
[*]Everything else. 
[/LIST]

In discussing other things, the particulars of item 3 "byte code" and how it gets used can become very important. There are so many strategies because there are so many priorities and requirements.

> 
Also, what is this binary package that you keep referring to? Why the adjective? Why not just call it a package?

Some other types of packages would be:
[LIST]
[*]Configuration files (text) 
[*]Source code 
[*]Examples (text) 
[*]Documentation (/usr/share/<package>) 
[*]Documentation (man pages) 
[*]Metadata (timezone information, internationalization) 
[*]Fonts (non-executable bitmaps or vector data) 
[*]Sounds 
[*]Themes for window managers 
[/LIST]

Surely there are other types of information which are put into packages fairly often.

---

### Post by freemedia2018 on 2019-04-22
Some of the things not answered yet. 

Richard Stallman is the primary author of the GNU GPL license. He also founded the FSF, who maintains the GNU project-- including this particular license. 

Any software project, whether under the GNU umbrella or not, can choose to license under the GPL. That doesn't make it part of the GNU project. I am not sure whether GNOME was ever officially part of the GNU project or not. Its politics/allegiances these days are different from that of GNU. It's not that nobody knows, it's that nobody here knows. The GNOME Foundation certainly knows and if you were involved with the project, you would know too. (It's not secret.)

Bytecode is a popular (but not mandatory) aspect of interpreting. When you find .pyc files, those are Python bytecode. You often generate them simply by running Python code with a .py extension.

Interpreted: bash, Python, perl... other languages are interpreted. You run the program WITH the interpreter. Sometimes it produces bytecode files, other times it translates to bytecode in RAM. If bytecode is used, the first step is to translate to bytecode, then the bytecode is interpreted. Otherwise, the source is interpreted directly.

Compiled: C, C++, Rust-- are compiled directly to binaries. Unlike interpreted code, you dont need the compiler to run the binaries. You only need it to create them from the source.

You can try interpreting some code with Python, and creating bytecode:

Run code directly from the command line: (interpreted)
```
python -c "print('hello world')"
```

Save to file and run:
```
echo "print('hello world')" > hw.py && python hw.py
```

Create bytecode: (done automatically, but this creates a .pyc file)
```
python -c "import hw"
```

Read each character of hw.py and give the ASCII code:
```
echo $(python -c "for each in open('hw.py').read(): print(ord(each))")
```

Read each character of hw.pyc (the bytecode) and give the ASCII code:
```
echo $(python -c "for each in open('hw.pyc').read(): print(ord(each))")
```

.pyc bytecode files are usually generated when a .py file is imported. This is how it works in Python, and each language does it differently.

Run bytecode directly:
```
python hw.pyc
```

---

### Post by 1clue on 2019-04-22
> **1clue said:**
> ...
Some other types of packages would be:
[LIST]
[*]Configuration files (text) 
[*]Source code 
[*]Examples (text) 
[*]Documentation (/usr/share/<package>) 
[*]Documentation (man pages) 
[*]Metadata (timezone information, internationalization) 
[*]Fonts (non-executable bitmaps or vector data) 
[*]Sounds 
[*]Themes for window managers 
[/LIST]

Surely there are other types of information which are put into packages fairly often.

More on this:
Most mainstream desktop distros will combine the various file types into the same package. Some minimalist distros will have one main package for executables and basic configuration, and have another for the man pages for example. So that a minimal VM can be created without any extra wasted space.

There is no requirement that a package have only one type of information in it, or even a tradition to do so. The package has a bunch of stuff in it which the packager thinks is relevant to the purpose of the package. It might be absolutely everything coming from the upstream application maintainer, or it may even have extra things they thought would be nice to have. So you can have ultra-skinny packages and need to install more packages to get the same thing, or you can have normal sized ones or you can have extra fat ones. IMO the most that a package should have is "everything upstream" and a sane, simple configuration active. No extras. If you want examples or extra glitter, you should be able to find it in a different package.

---

### Post by freemedia2018 on 2019-04-22
> **1clue said:**
> IMO the most that a package should have is "everything upstream" and a  sane, simple configuration active. No extras. If you want examples or  extra glitter, you should be able to find it in a different package.

+1, Be nice if more people thought that way. Most people who maintain packages seem to. Not everyone who maintains package managers do.

---

### Post by TheFu on 2019-04-23
> **freemedia2018 said:**
> +1, Be nice if more people thought that way. Most people who maintain packages seem to. Not everyone who maintains package managers do.

Developers often don't think like distros.
When I was writing code professionally, I wanted my projects self-contained under a single directory structure.  Something like this:
```
Program/
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; contrib
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9492;&#9472;&#9472; lib
```

That has been the way that Unix did things for 30+ yrs, then Linux came along and wanted to split all those places up - putting the programs in /usr/bin, the docs into /usr/share/, the config files into /etc/ and any libraries into /lib or /usr/lib/

Before the Linux distros came along, switching between different versions of a program, including all the libraries, docs, settings was managed with 1 symbolic link. Like this:
```
$ ls -Fl Program

lrwxrwxrwx 1 thefu  thefu   13 Apr 23 13:13 Program -> Program-2.0.0/

$ ls -F Program-*

Program-1.0.1:
bin/  contrib/  doc/  etc/  lib/

Program-1.0.2:
bin/  contrib/  doc/  etc/  lib/

Program-1.0.3:
bin/  contrib/  doc/  etc/  lib/

Program-2.0.0:
bin/  contrib/  doc/  etc/  lib/
```

Just change where "Program points" to completely change everything.  We can see something like this in /usr/local/.  There are issues with everything being self-contained, either a link to the program needs to be put into the PATH somewhere or the PATH needs to be extended for the new program.  Also, when everything was self-contained to a specific directory, removal of the specific version of the program was trivial. Just delete Program-1.0.1 and everything under it. 
The flaws with these sorts of setup is that dependencies have to be manually managed.  RPM and APT are huge leaps ahead on that and the main reason I switched to Ubuntu.  Dependencies and relatively easy patching.  If you've never had to manually handle dependencies to get a program working, it is hard to understand how complex that can become.

Data files would be stored either in a server-known location or for desktop programs, under the specific userid's HOME.  This is the same as it always was.  There is a package tool that handled these things called **epkg**.  Lots of slackware people use it still.

There are just as many complaints for GUI programs when program menus don't follow the other programs' style on any specific GUI.  In theory, the distros will handle that with themes or specific compile-time options.  Controlling the look-n-feel is something that the different GUI programming toolkits try to handle, but then there is another dependency for all the GUI programs. What happens when 25% of the programs use a different GUI toolkit?  Those programs look different and don't honor the themes.

And coming back to packages ... they include pre-install and post-install and removal scripts.  Without these scripts, it wouldn't be as easy to have 1 checkbox for "LAMP Server" install. That metapackage (there's another, better name for this, I just don't know it) does much more than just install Apache, MySQL and Php. It sets up the configs so they all work together.

In a few of my jobs, I wrote installation programs for many different platforms, including Windows, MacOS, and 12 different Unix systems.  Windows was the hardest, by far. It was almost a black-art because the tools were so poorly made at the time. We used a commercial tool - InstallShield.  There were 2 ways to copy a file into an installation, but only 1 of those actually worked. So many bad memories.  On the Unix platforms, the installations were relatively easy because I controlled the entire installation program.  These were for non-trival programs - N-tier servers and desktops - running on hundreds of clients and at least 5 servers back when each server was $200K or more.

Ok, sorry to interrupt.

---

### Post by freemedia2018 on 2019-04-23
> **TheFu said:**
> Ok, sorry to interrupt.

Not at all, I found it inspiring. I almost want to create a program to rearrange my system with that structure.

I wouldn't have to recompile everything, I would have to create a bunch of symlinks. Why? As a demo. Probably more work than I'm willing to put in, but I wasn't lying about the inspiring part. And I've barely touched Windows in 12 years, but I vividly recall InstallShield. "What is the point of this?" It transforms the pain of installing things in Windows into the pain of installing them with InstallShield instead.

---

### Post by TheFu on 2019-04-23
The reason for InstallShield wasn't about the installations. It was about the removals later.  With the way that Windows likes to put stuff in odd places (to me as a Windows programmer).

The symlink method is handy when you have a program to be installed, but with .deb packages, best to stick with the distro's decisions and learn those 5 special places, which happen to fit into the Linux File System Hierarchy standard.  All the major distros follow it.

If you move package installed files around, that breaks package management. Expect a full reinstall for any distro based on any of the package managers.  Look at Gentoo if that is what you want.

---

### Post by 1clue on 2019-04-23
I remember some of that directory madness, it was both elegant and clumsy depending on how you looked at it.

There are still some developer tools that use this approach, with the root being in the $HOME directory. For example, [https://sdkman.io/](https://sdkman.io/) . This is great if you have several different versions of a project which must be supported or tested simultaneously. You can easily script a tool to check your current development directory to find the expected version of a **foo**, and then switch the (current) shell over to that version of **foo**. Settings and everything follow over.

WRT Windows, I was always irritated by the registry. 

[LIST=1]
[*]That there was one file which held so much importance for pretty much everything on the hard drive.
[*]That in order to delete some apps you literally had to go in there with an editor and delete or modify many entries
[*]That if you messed it up, you could make the box so incredibly unbootable.
[/LIST]

Still to this day I oppose a single binary file like that. UNIX having text files as a standard for this sort of configuration is fantastic, although it's been decades since some commercial variants have adopted a binary registry-style configuration.

---

### Post by TheFu on 2019-04-24
> **1clue said:**
> 
WRT Windows, I was always irritated by the registry. 

[LIST=1]
[*]That there was one file which held so much importance for pretty much everything on the hard drive.
[*]That in order to delete some apps you literally had to go in there with an editor and delete or modify many entries
[*]That if you messed it up, you could make the box so incredibly unbootable.
[/LIST]

Still to this day I oppose a single binary file like that. UNIX having text files as a standard for this sort of configuration is fantastic, although it's been decades since some commercial variants have adopted a binary registry-style configuration.

I'm with you.  Text should be the default config solution. How do you feel about dconf and dconf-editor?

---

### Post by 1clue on 2019-04-24
> **TheFu said:**
> I'm with you.  Text should be the default config solution. How do you feel about dconf and dconf-editor?

I think I sufficiently covered that in my previous post.

[I]**Edit:** I don't mind an app having configuration in a database. Some apps, including some I've written, have complex configurations that can change on-the-fly. A database may be the best solution there.

My objection comes from having a single database which, when messed up, causes the entire system to be unusable for its intended purpose.
[/I]

---

