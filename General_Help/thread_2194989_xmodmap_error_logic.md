---
title: "xmodmap error logic"
date: 2013-12-21
forum: General Help
---

### Post by Tyndarus on 2013-12-21
Hello,

Whilst modifying keyboard layout, I'm getting an 'Error of failed request' quite often (see below).
Yet I mostly don't understand why this error message is generated. This makes it quite hard to write valid xmodmap expressions.

Would it be possible to explain why the following error occurs? This simple example: clear control; error; clear lock; clear control can be repeated with both shift and mod4 modifier key instead of control:

1: reboot, NO custom changes in xmodmap whatsoever. 

2: $ xmodmap -pm
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Shift_L (0x32)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

3: $ xmodmap -v -e 'clear control'
! 1:  clear control
        clear control
!
! executing work queue
!
        clear control
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0x17
  Serial number of failed request:  8
  Current serial number in output stream:  8

4:$ xmodmap -v -e 'clear lock'
! 1:  clear lock
        clear lock
!
! executing work queue
!
        clear lock

5: $ xmodmap -v -e 'clear control'
! 1:  clear control
        clear control
!
! executing work queue
!
        clear control

And POOF, it works...

I'm getting similar error (error of failed request) when using 'remove' and 'add'. (never had problems with keycode and keysym). Only for 'add' I understand the origin of the error:
"The problem arises when you try to add a keysym to a modifier which is  already added to another modifier key. It is vital to know, that if you  add a keysym to a modifier all other keysyms that companion the keysym  in case are added also as to that modifier."
([http://unix.stackexchange.com/questions/4485/reassign-ctl-and-alt-keys-xmodmap-error](http://unix.stackexchange.com/questions/4485/reassign-ctl-and-alt-keys-xmodmap-error))

Original problem was to make the space bar work as an additional ctrl key when held using "XCAPE"
([https://github.com/alols/xcape](https://github.com/alols/xcape)), this works now, but I also had to start with 
$ xmodmap -v -e 'clear lock'
for reasons beyond my understanding...

Could anyone explain the origin of this error message so I may understand how to use xmodmap correct (I've got a few more modifications to make...)? 

Thanks in advance (and eternal glory once you've given me a meaningful answer...)

Dieter VE

---

