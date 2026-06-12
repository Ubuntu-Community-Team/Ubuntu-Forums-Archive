---
title: "why do I get &quot;error: variable xxx has initializer but incomplete type&quot;  on compile?"
date: 2013-05-29
forum: General Help
---

### Post by mike35 on 2013-05-29
Hello, I have a kernel module I wrote and it runs on Red Hat Enterprise  Linux.  I am trying to port it to Ubuntu.  I tried to just load the  compiled version but it won't (insmod fails with "invalid module format"  which I pretty much expected)..  So I'm trying to recompile the source  on the Ubuntu system.  First I did "su -" then "apt-get install  module-assistant" which worked well.  Then I did "m-a prepare" which  looked mostly good but did give one error "couldn't create the  /usr/src/linux symlink".  Then I tried compiling which gave me a  compiler error message:

                              error: variable ‘Pdrive_Intf’ has initializer but incomplete type

In my code the variable 'Pdrive-intf' is 

struct file_operations Pdrive_Intf =    //ldd3-49, pdf-67
{
    read:        Pdrive_Read,
    write:        Pdrive_Write,
    ioctl:        Pdrive_Ioctl,
    open:        Pdrive_Open,
    release:    Pdrive_Release,
};


So I gather that "file_operations" is not defined? Does that mean I need another linux header file?   Any ideas on what I should try next?  Thanks,

-Mike

---

