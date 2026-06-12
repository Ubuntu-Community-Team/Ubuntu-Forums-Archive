---
title: "VIM Help Page"
date: 2021-09-10
forum: General Help
---

### Post by damirx on 2021-09-10
Hi,

Hope this is the right place to post and ask my question.

Problem: Cannot access the help pages inside VIM. I am running VIM version 8.2.2434 in Ubuntu 21.04. 

When I enter a :help in the command-line mode I get:

E433: No tags file
E149: Sorry, no help for help.txt.

When I go to /usr/share/vim/vim82/doc[I] I do see a help.txt though. I am not clear about this.

I would appreciate some help.

Thank you.[/I]

---

### Post by TheFu on 2021-09-10
Run **vimtutor**.  That's a command.

If :help doesn't work, I suspect you don't have the full vim install. There are multiple packaged versions - vim-tiny, vim-basic.  I think you need the full, "vim" package for the most common stuff.

---

### Post by damirx on 2021-09-10
Awesome. I did not know that command. I removed vim-tiny package and left the full one.

May also ask you if you know why the color scheme that I defaulted on my .vimrc file in my /home directory and help section are only available when I open vim with root priviledges? This does not happen to me in CentOS for example, which I am more familiar with. 

Thanks again.

---

### Post by scorp123 on 2021-09-11
> **cyberpurity said:**
> why the color scheme that I defaulted on my .vimrc file in my /home directory and help section are only available when I open vim with root priviledges?

What are the permissions on that ~/.vimrc file?  Check with:
```
ls -al .vimrc
```

---

### Post by TheFu on 2021-09-11
Yet another reason that using "sudoedit" and not "sudo vim" or "sudo gedit" is the preferred method.  Check permissions.

CentOS and Ubuntu are different. They have different goals and subtle differences outside the package management differences.  Isn't CentOS out of support?

---

### Post by scorp123 on 2021-09-11
> **TheFu said:**
>  Isn't CentOS out of support?

CentOS 6 is EOL/EOS. CentOS 7 is still good until 2024. CentOS 8 will switch to a rolling release model after 31 December 2021 and become "CentOS Stream 8".

So instead of the old release chain / upstream-downstream relationship that looked like this:
Fedora => Red Hat Enterprise Linux => CentOS

... we will now get this:
Fedora => CentOS Stream => Red Hat Enterprise Linux

That's one of the reasons why many former CentOS users are looking at alternatives so they could replace CentOS 8. "Rolling release" is just a big fat "NOPE!" in an Enterprise environment.

---

### Post by damirx on 2021-09-11
> **scorp123 said:**
> What are the permissions on that ~/.vimrc file?  Check with:
```
ls -al .vimrc
```


The file belongs to the regular user in question (both uid and guid). Permissions are 755.

---

### Post by TheFu on 2021-09-12
Which release are you running?  sudo behaves different on new Ubuntu releases than it did on olders releases and those are different from other linux distros default behavior.  The parent directory permissions matter too. Please show the output.

---

### Post by damirx on 2021-09-12
> **TheFu said:**
> Which release are you running?  sudo behaves different on new Ubuntu releases than it did on olders releases and those are different from other linux distros default behavior.  The parent directory permissions matter too. Please show the output.

Here is it is. Thank you for your help.

---

### Post by TheFu on 2021-09-12
21.04 is too new for me.  I think ssh behavior in Ubuntu changed.  Track those changes down. I couldn't find any easily, but vaguely recall a discussion, somewhere, about the changes.  I think the HOME directory was being set now, when it wasn't touched previously. Sorry I couldn't find a link.

Please post text, not images. People with poor eyesight and some people pay for internet by the byte.  300 bytes is much nicer than 40Kb.

---

### Post by damirx on 2021-09-12
> **TheFu said:**
> 21.04 is too new for me.  I think ssh behavior in Ubuntu changed.  Track those changes down. I couldn't find any easily, but vaguely recall a discussion, somewhere, about the changes.  I think the HOME directory was being set now, when it wasn't touched previously. Sorry I couldn't find a link.

Please post text, not images. People with poor eyesight and some people pay for internet by the byte.  300 bytes is much nicer than 40Kb.

I understand. I will do that. And will also keep the thread open for now. I appreciate your help.

---

### Post by damirx on 2021-09-30
> **damirx said:**
> Here is it is. Thank you for your help.


Hello friends. 

I simply went back to Focal Fossa where these problems are not a thing. 


Thank you.

---

### Post by QIII on 2021-09-30
Removing the SOLVED tag.

You avoided the issue.  You didn't solve it.  For the sake of others who may see the SOLVED tag and think the thread offers a solution, please do not mark threads solved unless they actually are.

Thanks.

---

### Post by damirx on 2021-09-30
> **QIII said:**
> Removing the SOLVED tag.

You avoided the issue.  You didn't solve it.  For the sake of others who may see the SOLVED tag and think the thread offers a solution, please do not mark threads solved unless they actually are.

Thanks.

Hi Qlll,

Perfect. Actually I was not sure if I could leave it open undefinitely until the issue gets to be actually resolved.

Thanks for letting me know. 

Regards.

---

