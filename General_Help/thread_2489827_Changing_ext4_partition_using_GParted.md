---
title: "Changing ext4 partition using GParted?"
date: 2023-08-10
forum: General Help
---

### Post by Drone4four on 2023-08-10
I asked ChatGPT if it was possible to change the partition size of an ext4 file system using GParted. I was provided with instructions (see below) but I am stuck at Step #4. After I select the ext4 partition and right click, when I select &#8220;Resize/Move&#8221;, changing the size isn&#8217;t possible. See attached for an image of what GParted looks like to me. What am I doing wrong? Is it possible to change the size and shrink or reformat an existing partition without having to reinstall my operating system and starting from scratch?

> Yes, you can achieve the same outcome using the graphical partitioning tool GParted. GParted provides a user-friendly interface for managing partitions and filesystems, making it a popular choice for resizing ext4 filesystems and partitions. Here's how you can use GParted to resize an ext4 filesystem and partition:
**1. Install GParted: **
If GParted is not already installed on your system, you can install it using your package manager. For example, on a Debian-based system, you can use the following command:
bash
```
$ sudo apt-get install gparted
```
**2. Open GParted: **
Launch GParted from your system's application menu or by running sudo gparted in the terminal.
**3. Select the Target Drive: **
Choose the drive that contains the ext4 filesystem and partition you want to resize from the drop-down menu in the top-right corner of the GParted window.
**4. Shrink the Filesystem: **
Right-click on the ext4 partition you want to resize and select "Resize/Move." In the Resize/Move dialog, you can adjust the size of the filesystem by dragging the partition boundary or by entering the desired size. This step resizes the ext4 filesystem to make space for the new partition.
**5. Apply the Changes: **
After resizing the filesystem, click the "Apply" button in GParted to apply the changes. GParted will execute the filesystem resize operation.
[B]6. Resize the Partition: 
[/B]Once the filesystem resize is complete, you can again right-click on the partition and select "Resize/Move." Adjust the partition size to use the newly allocated space, either by dragging the partition boundary or entering the size manually.
**7. Apply the Changes: **
Click "Apply" to execute the partition resize operation. GParted will adjust the partition size to match the new size of the ext4 filesystem.
**8. Resize the Filesystem Again (Optional): **
If the partition size was increased, you might want to resize the ext4 filesystem to use the entire partition. Right-click on the ext4 partition and choose "Resize/Move." Then, expand the filesystem to fill the entire partition and apply the changes.

Remember that whenever you are working with partitioning and filesystem operations, there is a potential for data loss if not done correctly. It's always a good practice to back up your important data before making any changes. Additionally, understanding the tools and the process thoroughly is essential to avoid unintended consequences.


---

### Post by Dennis N on 2023-08-10
All your partitions are mounted. You have to unmount the partition you want to change, then you can shrink or enlarge. In this case, you need to work from live media.

---

### Post by Rubi1200 on 2023-08-10
> **Dennis N said:**
> All your partitions are mounted. You have to unmount the partition you want to change, then you can shrink or enlarge. In this case, you need to work from live media.
+1!

And ALWAYS **backup **before doing anything with partitions.

---

### Post by SeijiSensei on 2023-08-11
Boot from an [installation image]("http://cdimage.ubuntu.com/ubuntu/releases/22.04.3/release/") and go to the desktop rather than installing.. Then install and run gparted. Linux will be running from the root of the installation image, and your drive will not be mounted.

---

### Post by ajgreeny on 2023-08-12
Gparted is available by default, ie, already installed in all of the Ubuntu family of live systems so no need to install it manually after booting the live system.

All other comments are correct!

---

### Post by SeijiSensei on 2023-08-13
By default, KDE systems like Kubuntu ship with the KDE Partition Manager. I suspect it's just a front-end to gparted, but gparted itself may not be available in this flavor.

---

### Post by ajgreeny on 2023-08-13
I've not used Kubuntu so wasn't aware of that so thanks for the info Seiji.

---

### Post by Drone4four on 2023-08-21
> **Dennis N said:**
> All your partitions are mounted. You have to unmount the partition you want to change, then you can shrink or enlarge. In this case, you need to work from live media.

To close the loop one week later: This is the answer I needed. This makes 100% sense. I should have thought of this. Thank you, Dennis.

---

