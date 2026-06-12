---
title: "How to install vmware2libvirt"
date: 2008-06-06
forum: General Help
---

### Post by prickly on 2008-06-06
I have installed KVM on my GNOME Ubuntu (Hardy) desktop to convert a VMWare virtual machine to KVM.

From what I have found online it seems that vmware2libvirt is not currently shipped with the KVM binaries. 

I have however found that it can be downloaded from here: [http://people.ubuntu.com/~soren/vmware2libvirt/](http://people.ubuntu.com/~soren/vmware2libvirt/)

As yet I have been unable to find any explanation of how to "install" it. 

If I am in the same folder as these two files and I try to run vmware2libvirt it says: command not found.

I tried copying the files to \etc\libvirt to see if that would work.

Can anyone help with this please?

TIA
prickly

---

### Post by plumcreek on 2008-06-24
vmware2libvirt is a python script.

It's not something you "install" in the traditional sense.

To run it, you first need to make it executable like so:

```
chmod 755 vmware2libvirt
```You can now run it from the directory it is in like so:

```
/path/to/vmware2libvirt -f /path/to/config.vmx
```Or you can copy it to a directory that is in your path so that you can run it from anywhere on the system:

```
sudo mv -iv vmware2libvirt /usr/local/bin/
vmware2libvirt -f config.vmx
```

I hope that helps.

---

