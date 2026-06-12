---
title: "how can a non-root user get a source package"
date: 2023-03-20
forum: General Help
---

### Post by Skaperen on 2023-03-20
how can a _non-root user_ get a source package when [FONT=courier new]_/etc/apt/sources.list_[/FONT] has no _deb-src_ lines (this user can read [FONT=courier new]_/etc/apt/sources_[/FONT] OK) and the admin refuses to change that file?  i see no options to use a different _sources.list_ file.

---

### Post by MAFoElffen on 2023-03-20
Even if an admin added deb source lines to sources.list, an non-admin user would not be able to use apt to use deb source repo's.

A non-admin user could directly download source code from a net source to their own home directory and edit it there... But not be able to install it to the system after it was compiled.

In the commercial/business world, a non-admin user would submit those things as a "job" in the que.

Just what "are" you asking and wanting to do?

---

### Post by Skaperen on 2023-03-21
the goal of the non-root user is to examine the source code to understand more finely just how it does what it does.  based on a quick examination of the man pages the source deb would go into the current directory.

i AM the admin.  i just don't want to use root or sudo for anything like this.  if it does unexpected things i want to have that "i am not root" safety boundary.  it could fill up my file system but i know where i am doing this and should be able use the power of **[FONT=courier new]rm[/FONT]** under the same user to clean it up.  it is good practice to avoid using root for everything that does not specifically need root powers.  i am not installing anything from here.  my plan was to make a deb file and let root install it.

---

### Post by MAFoElffen on 2023-03-21
Just Noting that: There may be a translation problem of what you are trying to discuss. Which speaking "tech" does not always translate well between languages.

As an Administrator, which I have worked as such, for non-root users, I would setup a local code repository, and a test environment... Where a non-admin user could review, examine and test code, that would not affect production systems. Give then the power to do things, but in a sandbox, where it is safe. Deb Installation files, after being built and tested, then get reviewed and moved to production. 

You are correct in that sudo privileges should not be used for everything, but Debian installation files do cross over into needing those to "install. That is just how that works.

Does that proposed practice sound logical, secure, and safe?

I have worked as an Administrator, Database Admin, Developer, Network Admin, Tech Support. I have published deb files. It's not as basic as your are putting that (I am assuming that might be a translation difference), though I welcome you to your journey.

---

### Post by DuckHook on 2023-03-21
Is there an overriding reason that you wouldn't want to do this in a VM? VMs are designed to do exactly what you are trying to achieve: sandbox an app so that you can test it (including examining its source) without compromising your host installation.

While it may be possible to take extraordinary measures to set up a non-root environment for .deb installation, what would this gain you that a VM would not?

---

### Post by MAFoElffen on 2023-03-21
+1 with DuckHook. That is "how" I setup test environments for users. They can destroy the heck out of the VM guest system in a test, and it really doesn't matter. I can restore the VM for them and they can continue.

When I am compiling source on something I am not familiar with, I will setup up a DEV VM to build and install the source, and do testing to see how and what it did. A lot safer to do it that way that "live". For example Linux Kernel 6.3 & 6.4 and ZFS kernel modules... I would rather test that on a VM than on one of my main physical systems.

And when I am building deb packages, I will test them on VM's to make sure they are doing what I want them to do before I upload the deb packages to Launchpad.

---

### Post by Skaperen on 2023-03-23
a VM was already considered.  it can have performance issues.  what about a container?

---

### Post by DuckHook on 2023-03-23
> **Skaperen said:**
> a VM was already considered.  it can have performance issues.
True. Depends on what app you wish to run. Most aren't a problem. Only limitation is old or underpowered HW, or very demanding apps like games.
> ... what about a container?
Avoids many of the problems of VMs but creates some of their own.

[LIST]
[*]Not as secure as VMs.
[*]Docker is easier to use but less secure than LXD. At least, it needs special configuration to be more secure.
[*]LXD is more secure than Docker out of the box but harder to setup. That said, I don't consider it prohibitively hard.
[*]I'm not familiar with Docker, but LXD instructions are in my sig.
[/LIST]
I like the idea of containers for your use case. I did not recommend initially only because VMs are easier to implement and a bit more secure (which was your requirement), but I use containers almost exclusively and am comfortable with their sandboxing.

---

### Post by Skaperen on 2023-03-25
ideally, i would have liked to see a package tool that supported non-root users by doing things in that user's context.  if the user installs a package, it is placed in the user's home directory ready to use right there.  a document would exist for the end-user to customize their environment to work with this (such as what to include in PATH).  source packages would ha a place to put files (and to get them and user mods to build binary packages).  the user might have their own **[FONT=courier new]~/.etc/packages.list[/FONT]** file that can have different sources.

---

### Post by MAFoElffen on 2023-03-26
> **Skaperen said:**
> ideally, i would have liked to see a package tool that supported non-root users by doing things in that user's context.  if the user installs a package, it is placed in the user's home directory ready to use right there.  a document would exist for the end-user to customize their environment to work with this (such as what to include in PATH).  source packages would ha a place to put files (and to get them and user mods to build binary packages).  the user might have their own **[FONT=courier new]~/.etc/packages.list[/FONT]** file that can have different sources.
I have experience as a Systems Engineer, Database Administrator, Network Administrator, Developer, and IT consultant. Let's get out of generalizations / abstracts and start talking about some details.

- What languages are you talking about your people developing in? Python, C, C++, BASH? Your developers have and experience based in what?

- For applications? Or systems types of software? Are you wanting to do patches on something that exists? Or new development?

- What types of packages are you referring to. You said said installing, which for apt and dpkg would require admin rights to install... Which would require a DEV/TEST environment, usually a VM or container, that you could give a developer admin rights to install and control the env of. That would be a Debian package type, which then, which Section Type of deb package?

If a Snap's style of package that could be installed as an end-user, then we are talking about a different environment. That could be something out of the Snap Store...

- What part of which environment are you talking about that you want to give them control over?

Because in what you have said, that could be misinterpreted as being anything from being a VM or container, to being a development virtual environment in an IDE or as simple as a mapped Python virtualenv.

That could be many paths, for what your understanding that you are trying to describe may be completely different.  Please paint a picture, that we can visualize. I think both DuckHook and I are reaching to guess what might fill your needs, because we are missing those details that would narrow that down to a defined path.

---

### Post by Skaperen on 2023-03-27
> **MAFoElffen said:**
> I have experience as a Systems Engineer, Database Administrator, Network Administrator, Developer, and IT consultant. Let's get out of generalizations / abstracts and start talking about some details.
i'll try

> **MAFoElffen said:**
> - What languages are you talking about your people developing in? Python, C, C++, BASH? Your developers have and experience based in what?
just about any.  even some sometimes work in assembly.  sometimes more than one for one project for the same client.

> **MAFoElffen said:**
> - For applications? Or systems types of software? Are you wanting to do patches on something that exists? Or new development?
it varies by project/client.

> **MAFoElffen said:**
> - What types of packages are you referring to. You said said installing, which for apt and dpkg would require admin rights to install... Which would require a DEV/TEST environment, usually a VM or container, that you could give a developer admin rights to install and control the env of. That would be a Debian package type, which then, which Section Type of deb package?
i don't understand this question enough to form an answer.

> **MAFoElffen said:**
> If a Snap's style of package that could be installed as an end-user, then we are talking about a different environment. That could be something out of the Snap Store...
Snap appears to possibly be a better way to install or deploy things for customers but i haven't done that, yet

> **MAFoElffen said:**
> - What part of which environment are you talking about that you want to give them control over?
their non-root user space on a single server in early evaluation of a project (before the client offer/bid).

> **MAFoElffen said:**
> Because in what you have said, that could be misinterpreted as being anything from being a VM or container, to being a development virtual environment in an IDE or as simple as a mapped Python virtualenv.
this is before development begins.

> **MAFoElffen said:**
> That could be many paths, for what your understanding that you are trying to describe may be completely different.  Please paint a picture, that we can visualize. I think both DuckHook and I are reaching to guess what might fill your needs, because we are missing those details that would narrow that down to a defined path.
this is a project evaluation to determine or guess what is needed such as development language, developer time, testing resources, regulatory requirements, security issues, and so on.  results of initial research are usually evaluated by others.  the final result is usually a cost figure or a recommendation to decline.

my original question was a single point.  it seems the answer is that non-root is not implemented.  perhaps a cloud instance would be a way to go.  they are cheap enough. or some spare laptop.  or the VM.

---

### Post by MAFoElffen on 2023-03-27
I have Raspberry Pi4 that I run Ubuntu Server (with an installed Desktop) on with KVM and LXD. It doesn't take much. That is also the machine that I do my work on the UbuntuForums 'system-info' Script maintenance, and manage the DEV/TEST and STABLE repo's from it. I should noted, that I boot it via USB from a large NVMe drive.

For code version control systems, I use Git and Bazaar.

I do most my detailed testing on it and on my laptop, from my main KVM server. I do most of my testing of the 'system-info' script on VM's, though have a branch that is targets towards containers. 

I have other scripts in the Ama-Gi Project that are mostly Python. The editors / IDE's that I mostly use are Eclipse, and Visual Studio. Eclipse has pluggins for Bazaar and Git. Visual Studio has no integration with Bazaar, but has a pretty good integrated hooks for Git. 

My experience base in languages is (not-inclusive / summarized) Assembler, BASIC, C, COBOL, C++, C#, VBA, VisualBasic, SQL, Python, BASH, PowerShell, HTML5, CSS3, Java, Javascript, XTML, Spectra,  etc. On many different platforms. My choices have been based off my experience.

As having a broad experience base beyond just "applications" (systems, database, networking, etc.) I know how the pieces work and how they should fit together... Come up with a solution that is scalable. It can start out on a laptop, to server, to private cloud, to cloud... 

Next, if you do not know what package types "are" (deb, rpm, snap, flatpak, msi, etc) or packaging systems (apt, dnf, pacman, zypper, etc), then I think you need to do some research into what might be needed to facilitate building them.

You are asking what you think is a single question, for your company. But as a commercial endeavor, there are many factors, that affect an answer.

*** Yes, you could just create a network share and give anyone access to 'source code'. They are just files. That is a simple, short answer. As as System Admin, then the flood of other factors start to come into play. As a start, how to manage what is there. What is done with it. Etc. Etc. Etc. Etc.

That is just my thoughts on that.

---

