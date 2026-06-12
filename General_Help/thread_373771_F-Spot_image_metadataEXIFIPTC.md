---
title: "F-Spot image metadata/EXIF/IPTC"
date: 2007-03-01
forum: General Help
---

### Post by canter690 on 2007-03-01
Hi

I am using F-Spot to manage my photo's and it has nicely sorted images by date at least in the most part.

I have a number of images created by and old Sony Mavica camera which I didn't think stored any image metadata.  Exiv2 and jhead tell me there is no exif information in the images yet F-Spot is able to sort the images by date and time.  The time stamp on the file does not correlate to time the image was taken so I don't believe F-Spot is getting the data from there.

My main concern is that although F-Spot can sort and show the images on its time line feature the files are actually stored in wrong directory on disk.  F-Spot has a nice mechanism of creating a YEAR/MONTH/DAY structure for its images.  The old Mavica jpegs were actually taken in the year 2000 but are being stored in the 2006 subdirectory.

Can any one shed light on how F-Spot is able to determine the date and time of these old images and why its not storing them in the right directory.

Cheers

---

### Post by jongkind on 2007-03-02
In the case that you describe (absent metadata) F-spot uses the time-stamp of the file itself.

---

### Post by canter690 on 2007-03-02
What is confusing is that within F-Spot the image is shown as having a date   in October 2000.  The time stamp shows November 20th 2006 which is where the file is stored.  What I don't understand then is where is it getting the image date of October 2000 from ( which is actually the correct date when the image was taken ).

---

