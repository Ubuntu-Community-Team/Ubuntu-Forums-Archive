---
title: "GPSD with Garmin GPS"
date: 2008-07-07
forum: General Help
---

### Post by HABalloonGirl on 2008-07-07
Hi all,

I'm new at this whole thing using GPSD and I'm having a few problems.  I have a piece of C code like gpspipe that stores the NMEA data from my GPS in a log file.  That part works just fine.  The problem comes when I try to do something like

int main(){
        char *server=NULL;
        static struct gps_data_t *gpsdata;
        struct gps_fix_t *gpsFix;

  if (!(gpsdata = gps_open(server, "2947"))) {
    fprintf(stderr, "no gpsd running or network error (%d).\n", errno);
    exit(2);
  }
         gpsFix = &gpsdata->fix;
  gpsdata->fix.mode=MODE_3D;
  gps_query(gpsdata, "rw\n");

  gps_poll(gpsdata);


        cout << "Mode:" << gpsdata->fix.mode << endl;
  cout << "Latitude:" << gpsdata->fix.latitude << endl;
  cout << "Longitude:" << gpsdata->fix.longitude << endl;
  cout << "Altitude:" << gpsdata->fix.altitude << endl;
        gps_close(gpsdata);

}  

I would really like to print out just the latitude etc. when I ask.  If I don't set the mode, it comes out as 0.  I get nan for all the other fields.  Is it b/c I don't have a fix?  Funny thing is, 1 out of 15 times I do this, I actually get the correct altitude etc.  I'm running my GPS on simulator mode which means I should always have a fix I think.  Does anyone have suggestions?  Can I make this method work or do I need to start working on my own functions to get the data I want?  If I do, does anyone know where there is some sample code like that? 
Thanks much.

---

