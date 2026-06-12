---
title: "How to get all data of an Ubuntu Touch Nexus 7 Flo?"
date: 2023-12-24
forum: General Help
---

### Post by norvel4 on 2023-12-24
I have a Nexus 7 Flo 16GB running Ubuntu Touch 16.04 with no password of any kind and data I programmed on it. I would prefer to get all data off it. Home directory in like any machine readable format like files with all timestamps and a system image. I have two Windows 10 computers and one Ubuntu Pro (Ubuntu LTS 22.04.3) computer to work with. I also have large USB sticks. I tried to tar home directory, fail, I tried rsync and cp on like my Ubuntu computer, fail, I tried straight copy to computers, fail. Like my problem is created at is always current time even when I tar it. This is what I used to tar.

tar -p -czvf archive.tar.gz .

I did that in home directory then moved it to Music. I was thinking try this and like a Windows computer to copy again.

tar -czpvf Music/name.tar.gz --exclude="Music/*.tar.gz" ~/

I think I would run that in terminal at home directory of that tablet. What should I try? I am trying for a safe way to get all like my Home directory data then make a system image with all data on that device. I would also prefer a way to verify data is correct. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by norvel4 on 2023-12-29
I made a Ruby program that recorded all timestamps and used it so now I have all timestamps. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

