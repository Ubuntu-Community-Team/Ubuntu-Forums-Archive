---
title: "problem during write data to thermal printer using cups filter."
date: 2013-02-14
forum: General Help
---

### Post by saharanvikas8888 on 2013-02-14
I am using thermal printer(attached on usb port) and using cups 1.5.0. 
I  am developing on raster to label filter.In this,  CupsRasterReadPixels()  function returns successful value but  CupsRasterWritePixles() returns  fail value. If i remove  CupsRasterWritePixles() and replace with my own  code then printer gives  garbage printing. I want to use  CupsRasterWritePixles() but i have not  enough knowledge about  CupsRasterWritePixles().

**My code is:**

  while (cupsRasterReadHeader(ras, &header))
  {
   /*
    * Write a status message with the page number and number of copies.
    */
    if (Canceled)
      break;

    Page ++;

    fprintf(stderr, "PAGE: %d 1\n", Page);
    _cupsLangPrintFilter(stderr, "INFO", _("Starting page %d."), Page);

   /*
    * Start the page...
    */

    StartPage(ppd, &header);

   /*
    * Loop for each line on the page...
    */

    for (vertDot = 8, y = 0; y < header.cupsHeight; y++)
    {
     /*
      * Let the user know how far we have progressed...
      */

           if (Canceled)
           break;

           if ((y & 127) == 0)
            {
                     fprintf(stderr, "INFO: Printing page %d, %d%% complete...\n", page, (100 * y / header.cupsHeight));      
             }

     /*
      * Read a line of graphics...
      */

           if (cupsRasterReadPixels(ras, Buffer, header.cupsBytesPerLine) < 1)
           break;
           

     /*
      * Write it to the printer...
      */
       /* 
       Here i want to know that how i write data to printer using
       cupsRasterWritePixels()
        */
      
    }

   /*
    * Eject the page...
    */

    _cupsLangPrintFilter(stderr, "INFO", _("Finished page %d."), Page);

    EndPage(ppd, &header);

    if (Canceled)
      break;
  }

 I am not very experienced in write data to printer with using **CupsRasterWritePixels()**. So any insight is appreciated.
How do i solve this.

Thanks in advance.

---

