---
title: "Missing db libraries. Please help"
date: 2007-05-08
forum: General Help
---

### Post by AndrewGene on 2007-05-08
This is part of my results when i try to ./configure one of my files (pvfs-2.6.3)...

checking for struct xtvec in kernel... no
checking for struct kmem_cache in kernel... no
checking for SLAB_KERNEL flag in kernel... no
checking for memory_backed in struct backing_dev_info in kernel... no
checking for find_inode_handle callback in struct super_operations in kernel... no
checking for i_blksize in struct inode... no
checking for statfs_lite callback in struct super_operations in kernel... no
checking for fill_handle callback in struct inode_operations in kernel... no
checking for getattr_lite callback in struct inode_operations in kernel... no
checking for get_fs_key callback in struct super_operations in kernel... no
checking for readdirplus member in file_operations structure... no
checking for readdirplus_lite member in file_operations structure... no
checking for readx member in file_operations structure... no
checking for writex member in file_operations structure... no
checking for aio support in kernel... no
checking if statfs callbacks' arguments in kernel has struct dentry argument... no
checking if get_sb callback in kernel has struct vfsmount argument... no
checking for xattr support in kernel... no
checking for 6th argument to sysctl proc handlers... no
checking for linux/posix_acl.h... no
checking for linux/posix_acl_xattr.h... no
checking for linux/xattr_acl.h... no
checking for linux/mount.h... no
checking for linux/ioctl32.h... no
checking for linux/compat.h... no
checking for linux/syscalls.h... no
checking for asm/ioctl32.h... no
checking for generic_file_readv api in kernel... yes
checking for generic_permission api in kernel... yes
checking for generic_getxattr api in kernel... yes
checking for arg member in read_descriptor_t in kernel... no
checking for second arg type int in address_space_operations releasepage... no
checking for int return in inode_operations follow_link... no
checking for older int return in invalidatepage... NO
checking for warnings when including linux/config.h... yes
checking for compat_ioctl member in file_operations structure... no
checking for int return value of kmem_cache_destroy... no
checking for combined file_operations readv and aio_read... yes
checking for kzalloc... no
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking for epoll functions... checking whether cc is an Intel compiler... no
checking for db library... configure: error: could not find DB libraries.....

are these general libraries that are just missing??? I've been able to find some of them.  I have gcc+ 4.x.x (or something like that).  

any help would be GREATLY appreciated

---

### Post by lloyd_b on 2007-05-08
> checking for db library... configure: error: could not find DB libraries.....

are these general libraries that are just missing??? I've been able to find some of them. I have gcc+ 4.x.x (or something like that).

The error message isn't very helpful, but I'm guessing it's looking for the Berkeley DB library.

What I suspect is that you have the library itself installed, but the ./configure is looking for the development headers (which you *don't* have installed).

So my suggestion would be to install the package "libdb4.3-dev", to install the headers.  If by some chance you don't already have the library itself installed, then installing the "-dev" package should automatically trigger it's installation..

Lloyd B.

---

### Post by AndrewGene on 2007-05-08
Thanks.  That was exactly what it was.

---

