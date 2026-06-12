---
title: "XSane scans are offset, scan area not correct"
date: 2013-08-01
forum: General Help
---

### Post by nathandetroit on 2013-08-01
Anyone have suggestions on solving this issue?

Using Xsane to scan photos, I am seeing the following problems:

First I run a preview scan and select in the preview window the area to be scanned. When I next run a full scan, instead of scanning the selected area, the area scanned is displaced slightly to the right and down.

Also, the scan area shown in the preview window is only about 8.3" wide, when it should be 8.5" wide.

Other than the above, the scans work as expected. I have tried the following:
   - numerous configuration settings
   - uninstalled and reinstalled the MFC-440CN scan driver
   - deleted the .drc file in the .sane directory, and recreated it

As a work-around, I have been using GIMP to run the scans by selecting an area in the preview window larger than needed, and then using GIMP to crop to the right size - this works but takes a lot of extra time. 

Edited to add: I also tried another Brother printer-scanner I have, and had the same issue, so I think this rukes out a hardware problem.

Using Ubuntu 12.04 (64 bit)
Printer/scanner: Brother MFC-440CN (USB connected)
Edited to add: My scanner is using the Brother brscan2 driver.

Edited to add: Tested with an HP Photosmart printer/scanner and XSane. Did not see any of the above issues. Seems likely there is a problem with the Brother brscan2 driver, but this is not yet confirmed.

---

### Post by pqwoerituytrueiwoq on 2013-08-01
try the scanner front end in my signature, the back-end uses SANE
* it has a built in editor if you need it
if it has the same issue it is likely a driver bug

---

### Post by nathandetroit on 2013-08-04
Thanks for your interst. However, I have tried a couple of other scanning programs (all using SANE for the back end), and have the same problem with all of them. 

At this time I am thinking that the problem is with the Brother brscan2 driver. I have emailed Brother about this issue - have not heard anything back (amd I am not optimistic that I will get a response). If I do get a response from Brother, I will post an update here.


Update Aug. 9, 2013: I am corresponding with Brother via email on this issue, but as of yet there is no resolution. I will post further updates later.

Update Aug. 17, 2013: After several back and forth emails with Brother, I have convinced them that there may be a driver problem, and they have forwarded the issue to their engineer group for investigation. I will post further updates when I receive more information. I would also like to note that nothing posted here should be interpreted as a negative criticism of Brother. Even though Brother does not officially support Linux, they maintain a set of drivers (and related web pages with instruction and advice) on using their hardware with Linux. Although I would very much like to see Brother officialy support Linux, they do go a lot further than many other companies in providing Linux support. 

> **pqwoerituytrueiwoq said:**
> try the scanner front end in my signature, the back-end uses SANE
* it has a built in editor if you need it
if it has the same issue it is likely a driver bug

---

### Post by bl1ndm0nk on 2014-07-04
> **nathandetroit said:**
> Thanks for your interst. However, I have tried a couple of other scanning programs (all using SANE for the back end), and have the same problem with all of them. 

At this time I am thinking that the problem is with the Brother brscan2 driver. I have emailed Brother about this issue - have not heard anything back (amd I am not optimistic that I will get a response). If I do get a response from Brother, I will post an update here.


Update Aug. 9, 2013: I am corresponding with Brother via email on this issue, but as of yet there is no resolution. I will post further updates later.

Update Aug. 17, 2013: After several back and forth emails with Brother, I have convinced them that there may be a driver problem, and they have forwarded the issue to their engineer group for investigation. I will post further updates when I receive more information. I would also like to note that nothing posted here should be interpreted as a negative criticism of Brother. Even though Brother does not officially support Linux, they maintain a set of drivers (and related web pages with instruction and advice) on using their hardware with Linux. Although I would very much like to see Brother officialy support Linux, they do go a lot further than many other companies in providing Linux support.

Hi, did you get anything from Brother,  Thanks.

---

### Post by KalleHeiman on 2014-09-22
I just detected same offset-problem with Xsane.
I think it's caused by pixel calculation mistake: Scan preview is made by screen serolution 72dpi but Xsane calculates scanning offset with 75 dpi resolution. (This is only my guess).
You can see that there is no offset upper left corner and it grows to right and bottom.

---

### Post by Li_Wu on 2015-09-17
I found certain scan resolutions (low res black&white I believe) to be not working (when export to .pdf), but most other settings work well. just find a proper one.

---

### Post by Bucky Ball on 2015-09-17
*Thread closed.*

Over a year old. Thanks for sharing, but please don't wake the dead. :)

---

