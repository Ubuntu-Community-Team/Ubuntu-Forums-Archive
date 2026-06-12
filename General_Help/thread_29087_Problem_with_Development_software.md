---
title: "Problem with Development software"
date: 2005-04-22
forum: General Help
---

### Post by Marcel Firlej on 2005-04-22
Hi all,

It is not programming problem but libraries problem...

I do not know what' going on 'cose i cannot create new projects using Anjuta and Glide... :|

I was check everythink but it' not working still :[

Glide when I pressin' "Build" button, showin' message window:
{
  Error running glade-- to generate the C++ source code.
  Check that you have glade-- installed and that it is in your PATH.
  Then try running 'glade-- <project_file.glade>' in a terminal.
}
So I was run this in terminal, and I seen that message agan... And Glide is Glade 2 for Gnome 2 with C++ libraries and widgets wrapers.
-------------------------------------------------------------------------
Anjuta now,

When I' creating new GNOME C++ project, Anjuta buildin'... and:
{
    [..] required directory ./intl does not exist 
    ***[ERROR]*** automake failed
}
So I was run in terminal, ./autogen and I seen that message again
---------------------------------------------------------------------------

I have autogen package, all Anjuta and Glide 2 for Gnome 2 packages, 4 vesions of g++ and 4 for gcc, and 200 MB additional libs...

Anyone know what' going on?

Help please   :(

---

### Post by lorap on 2005-04-23
i'd the same problems.all you've to do go to the synaptic and do the next:
1.System-->Administration-->Synaptic Package Manager
2.Settings-->Repositories
once you've the repositories window open mark all checkboxes possible regardless any warnings then press Settings button and mark all checkboxes again except Download Upgradable Packages.then press Ok button.some download process'll begin and once it completes press Reload button.
after all that you'll need each time go to the Search button write the next packages and once you get them picked up mark them for install:

libgnomeui-dev
gettext
autotools-dev
devs
intltool
cvs
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-ttf2.0-dev

p.s.:
that'd work cause i've done this for myself and it did help.
have a nice day!
pavel

---

### Post by Marcel Firlej on 2005-04-23
Ok, Thanks

I will try :>

---

### Post by Marcel Firlej on 2005-04-23
And again some problems   :(

Anjuta is workin' good - thanks

Glade not, and I know why   :-)   But I donna know what I need to install. In teory I have no  C++   plugins for Glade, 'cose Glade is buildin' C projects only. I was install some C++ wrappers for Glade before, and all other packages for Glade. But Glade not workin' still with C++.

And one more problem now. When I' compilin' "MY" projects, I have error:
{
  ld returned 1 exit status
}
After Ajnuta project buildin', when I' pressin' "build" to see what Anjuta did, this LD error is in console :( And no other errors... 

Do anyone know why?

It is queer   :|

Thanks
  Marcel

---

### Post by lorap on 2005-04-24
hi friend!
donno what could cause this fault cause i've created gui projects in anjuta and run them with no glade installed.look friend for the additional libraries for C including documentation.try to create windows on your own without anjuta that'd help you encounter a problem,let me know if you donno how to create gui without anjuta or glade.
have a nice day!
pavel

---

### Post by Marcel Firlej on 2005-04-24
Thanks :-)

But what did you mind by "dev" package? I have "devscripts" only.

What ever. LD error lookin' that:
{
[...]
/usr/lib/libgnomeuimm-2.0.so: undefined reference to `Gnome::Canvas::Item::item_construct(Gnome::Canvas::Group&, ...)'
collect2: ld returned 1 exit status
make: *** [lol] Error 1
Completed ... unsuccessful
}

And what is the best. A was write the simple code (Console Hello World) and I was ld error too.

I will try another way.

It's not my problem only [http://ubuntuforums.org/archive/index.php/t-21096.html](http://ubuntuforums.org/archive/index.php/t-21096.html)

Thanks

---

### Post by Marcel Firlej on 2005-04-26
Hi, it' me again

So I did what "lorap" said

This is little and simple source:
------------------------------------------------
#include <gnome.h>

int main(int argc, char *argv[ ])
{
  GtkWidget *ghosh;
  gnome_init("sample", "0.1", argc, argv);
  ghosh = gnome_app_new("sample", "My Window");
  gtk_widget_show(ghosh);
  gtk_main();
  return 0;
}
-------------------------------------------------------
and compilation:

# gcc myapp.c -o myapp `gnome-config --cflags --libs gnomeui`

result:

/tmp/cco3X02P.o(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I can`t programming for GNONE, and I realy do not know why  ](*,) 

Anybody help?

---

