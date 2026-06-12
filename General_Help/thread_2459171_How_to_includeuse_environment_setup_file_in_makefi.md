---
title: "How to include/use environment setup file in makefile"
date: 2021-03-12
forum: General Help
---

### Post by hooby3 on 2021-03-12
I'm looking at cross-compiling for Raspberry PI

I would like to do something like this in a Makefile:
TOOLPATH=/opt/toolpath
include $(TOOLPATH)/environment-setup-aarch64

When trying to run make, I get an error:
/opt/toolpath/environment-setup-aarch64:5: *** missing separator.  Stop.



I'm guessing this is the wrong way to do this.  Is there a way to use the environment-setup-aarch64 from within the makefile? 

("Normal use" is to run the script before calling the makefile, but I am trying to automate things as much as possible, and doing this within the Makefile would be very useful for my activity)

Thanks!

---

### Post by TheFu on 2021-03-12
The error appears to be on line 5 of the environment-setup-aarch64 file.
Fix that.

---

