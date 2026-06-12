---
title: "University dual-boot lab setup"
date: 2007-08-06
forum: General Help
---

### Post by yellowbkpk on 2007-08-06
Last year I pulled together a dual-boot environment for my university's computer science lab. Since the lab is used by both computer science and non-CS students (and the university's main OS is WinXP Pro), the default boot option was WinXP. Last year, we used Fedora on the Linux side of things, along with NIS for authentication, NFS for /home sharing, and e-mail for sharing files among classmates.

They're trying to pull together the disk images that they will duplicate on to all of lab computers right now, so I'm looking for any tips or best practices on running a lab full of dual boot machines. I'd like to switch over to running Ubuntu on both the server and the client machines, switch away from using NIS (because LDAP feels easier to administer), and use Samba to allow students to access their files from their Windows machines in the dorm.

How does your school or other similar institution handle this type of situation? What's the best way for students to share files among themselves and the professor? The CS faculty uses Moodle for the "classroom management" software, so it would be excellent if there was some sort of integration with that.

Thanks!
yellowbkpk

---

### Post by strabes on 2007-08-07
I don't know if this is an option for you but at my university each student has their own "ifolder." It's basically a network drive with a small amount of storage that is just for the student and which the student can access any time while connected to our campus's network.

Are you looking at some sort of "public" storage that can be accessed by a certain group of people as determined by each prof?

Interestingly enough, all of my university's "windows" machines in the labs, library, etc, actually run debian and virtualize windows fullscreen on top. They're almost unbearably slow to use, which is why I use the "guest" computers in the library which are just plain debian with gnome and openoffice.

---

