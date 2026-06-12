---
title: "How to install tk.pm"
date: 2007-08-20
forum: General Help
---

### Post by VigneshBaliga on 2007-08-20
Hi All, I am new here. Got ubuntu running on my Acer Laptop. 
I need to install tk.pm (package I guess), but not sure how to do it ?

I just tried this code ..and got the following result...
--------------------------
#!/usr/bin/perl -w
use Tk;
$mw = MainWindow->new;
$mw->Label( -text => "Hello, World!" )->pack;
$mw->Button( -text => "Exit", -command => sub { exit } )->pack;
MainLoop;
-------------------------
Result:
Can't locate Tk.pm in @INC (... perl path )
Compilation aborted: ...

I though of installing some/any application that will in turn install Tk (like tkcvs), but got the an error of some conflicting software and prompted me to use synaptic!!
I will really appreciate any help.

---

### Post by SPr on 2007-08-20
Hi,

do you need perl-tk installing? It is in the repos.

---

### Post by VigneshBaliga on 2007-08-21
Sorry!, But I dint understand that ! :(
Does that mean it is in the repository ?.. I mean in the CD or already installed ? I did not check the CD, but kind-of searched for any installed stuff, assuming path/environment issue..but found none.
Also, I had downloaded the Ubuntu, and then burnt a CD to Install.. so not sure if it has it ?

---

### Post by VigneshBaliga on 2007-08-21
Oh tried a lot of stunts and installed many junk to get the Tk installed, with no luck.. and finaly after good amount of search I found it here :lolflag:

[http://ubuntuforums.org/showthread.php?t=267299](http://ubuntuforums.org/showthread.php?t=267299)
Rely by:** lamego**
**sudo apt-get install perl-tk**

Strange.. Y'day when I searched, had got no result !! :confused:
...anyway, I am good to go...  thanks to all.

---

