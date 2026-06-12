---
title: "Ubuntu USB help"
date: 2023-09-24
forum: General Help
---

### Post by partlow on 2023-09-24
Looking for some help. I am more hardware then software.

From time to time I need to run the Ubuntu OS on an USB drive.

I use it to recover files from broken OS's and remove stuff that has embedded on the OS.

I want to build an USB drive with Ubuntu that has my tools and setup ready for the next time.

That way I don't have to download and tweak my setup every time.

Looking for some pointers any help will be great.

---

### Post by MAFoElffen on 2023-09-25
I used to work as a Certified Onsite Warranty Technician for Dell, HP and Lenovo. I had this for Windows-To-Go and a Persistent Ubuntu LiveUSB... That I used for diagnostics, repair and data recovery. I also had USB Flash drives setup with Vendor specific bootable diagnostics, firmware branding tools and other utilities.

First off, select flash drives that are quality USB3.2 with good read and write speeds. They are worth the money. Doing so will help boot in a reasonable time. USB2.0 are way too slow. I did mine with 32GB drives and larger (usually 64GB - 128GB), That way I could ensure that I didn't run out of room. 

Especially for Windows-To-Go, I only used Lexar branded drives. They have a little known utility that can convert their USB flash drives to appear as USB Storage drives so that OS'es can install to them without being blacklisted for OS installation. For installing Linux directly to one of those modified drives, makes it faster to boot, and the you can install to them as if they were any other USB storage drive. Not all USB drives can be modified to do that, that way. And only certain flash drives were certified for Windows-To-Go installations.

When I created just regular persistent LiveUSB drives, I created them with Rufus on Windows, but you could also use mkusb on Ubuntu.

If I was doing a lot of machines, I also kept two other drives. A USB portable drive, setup with easy2boot. You copy a libary of iso's to the drive, the setup to boot what you want to boot. I setup ISO's that had updates installed already, with the applications I wanted on them. Then it had plenty of room for recovering data.

The other storage device I carried in my notebook bag was a USB dual x M.2 NVMe drive enclosure. Fast data recovery and imaging.

I also kept spare USB Flash drives so if I needed something off my notebook, I could create it right there, onsite. I arrived onsite with 2 bags: My tool bag and my notebook case, with a folding hand truck, so I could carry them and any replacement parts that had been ordered. And to carry out any parts that needed to be returned to the Vendor for warranty.

---

### Post by joshua123456 on 2023-09-25
> **partlow said:**
> Looking for some help. I am more hardware then software.

From time to time I need to run the Ubuntu OS on an USB drive.

I use it to recover files from broken OS's and remove stuff that has embedded on the OS.

I want to build an USB drive with Ubuntu that has my tools and setup ready for the next time.

That way I don't have to download and tweak my setup every time.

Looking for some pointers any help will be great.

I think a program called Cubic is what you are looking for. [https://github.com/PJ-Singh-001/Cubic](https://github.com/PJ-Singh-001/Cubic)

---

