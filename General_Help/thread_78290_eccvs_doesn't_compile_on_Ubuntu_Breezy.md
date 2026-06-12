---
title: "eccvs doesn't compile on Ubuntu Breezy"
date: 2005-10-18
forum: General Help
---

### Post by kalifi on 2005-10-18
Hi

This is my first post here, that means that there is bunch of information about this great distro around here, congratulations =D>

The problem with eccvs came after the upgrade to Breezy, when I try running it the output is:

Segmentation fault

than I tried to run it with sudo:

(eccvs:28992): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

Because I've compile eccvs, I compile it again. Everything was fine with ./configure, but it stuck with make, the final lines are:

../extern/libextern.a(cvsgui_wire.o): In function `std::_Rb_tree<unsigned int, s td::pair<unsigned int const, _WireHandler*>, std::_Select1st<std::pair<unsignedint const, _WireHandler*> >, std::less<unsigned int>, std::allocator<std::pair<unsigned int const, _WireHandler*> > >::_M_insert(std::_Rb_tree_node_base*, std::_Rb_tree_node_base*, std::pair<unsigned int const, _WireHandler*> const&)':
/usr/include/c++/4.0.2/bits/stl_tree.h:795: undefined reference to `std::_Rb_tree_insert_and_rebalance(bool, std::_Rb_tree_node_base*, std::_Rb_tree_node_base*, std::_Rb_tree_node_base&)'
../extern/libextern.a(cvsgui_wire.o): In function `operator--':
/usr/include/c++/4.0.2/bits/stl_tree.h:196: undefined reference to `std::_Rb_tree_decrement(std::_Rb_tree_node_base*)'
collect2: ld returned 1 exit status
make[2]: *** [eccvs] Error 1
make[2]: Leaving directory `/home/miro/software/eccvs/eccvs-0.2.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/miro/software/eccvs/eccvs-0.2.0'
make: *** [all] Error 2

I hope that I provide enough information about my problem. 

Thank you

Miro

---

