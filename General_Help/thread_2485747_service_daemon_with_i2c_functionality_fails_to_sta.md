---
title: "service daemon with i2c functionality fails to start"
date: 2023-04-08
forum: General Help
---

### Post by andrewcra on 2023-04-08
Hi all,

I got into troubles again! Yeah I know it's Easter, so I do wish all of you a very Nice Easter Holiday! For me that just means more time for projects :-)

Anyway, here we go with the issue. I have a small 128x32 OLED at default I2C address 0x3C connected to my raspberry pi 4, running Ubuntu 22.04.
No I do have to acknowledge right away, I don't have the pull-up resistors (2.7k or whatever they are ) installed. So that could be an issue, but read on!


I created a python script to show general info on the OLED, as it is a neat way to see what is going on inside my Robot. The OLED shows
ip-address, CPU load and Temp, memory and HDD (SD) utilization.

Very neat, works like a charm if I manually launch it.

So I created a service daemon as per usual:
```

/etc/systemd/system/oled.service
# -----------------------------------------------------------------------------
[Unit]
Description=OLED Display Service
After=multi-user.target

[Service]
ExecStartPre=/bin/sleep 30
Type=idle 
#ExecStart=/usr/bin/python3 /home/administrator/system_startup/oled.py
ExecStart=/usr/bin/python3 /usr/local/bin/oled.py

Restart=always
User=administrator

[Install]
WantedBy=multi-user.target

```

did restart service daemon via:
```
sudo systemctl daemon-reload
```

and made sure my python script is executable (even though it does get invoked with python3, so...) and can be found under 
```
/usr/local/bin/oled.py
# -----------------------------------------------------------------------------
import time
import subprocess

from board import SCL, SDA
import busio
from PIL import Image, ImageDraw, ImageFont
import adafruit_ssd1306


# Create the I2C interface.
i2c = busio.I2C(SCL, SDA)

#disp = adafruit_ssd1306.SSD1306_I2C(128, 32, i2c)
disp = adafruit_ssd1306.SSD1306_I2C(128, 32, i2c, addr=0x3C)

# Clear display.
disp.fill(0)
disp.show()

# Create blank image for drawing.
# Make sure to create image with mode '1' for 1-bit color.
width = disp.width
height = disp.height
image = Image.new("1", (width, height))

# Get drawing object to draw on image.
draw = ImageDraw.Draw(image)

# Draw a black filled box to clear the image.
draw.rectangle((0, 0, width, height), outline=0, fill=0)

# Draw some shapes.
# First define some constants to allow easy resizing of shapes.
padding = -2
top = padding
bottom = height - padding
# Move left to right keeping track of the current x position for drawing shapes.
x = 0


# Load default font.
font = ImageFont.load_default()

while True:

    # Draw a black filled box to clear the image.
    draw.rectangle((0, 0, width, height), outline=0, fill=0)

    # Shell scripts for system monitoring:
    cmd = "hostname -I | cut -d' ' -f1"
    IP = subprocess.check_output(cmd, shell=True).decode("utf-8")
    cmd = 'cut -f 1 -d " " /proc/loadavg'
    CPU = subprocess.check_output(cmd, shell=True).decode("utf-8").rstrip()
    cmd = "free -m | awk 'NR==2{printf \"M:%s/%s MB %.2f%%\", $3,$2,$3*100/$2 }'"
    MemUsage = subprocess.check_output(cmd, shell=True).decode("utf-8")
    cmd = 'df -h | awk \'$NF=="/"{printf "SD:%d/%d GB %s", $3,$2,$5}\''
    Disk = subprocess.check_output(cmd, shell=True).decode("utf-8")
    #cmd = 'sensors | awk \'/temp1/{print "T: " $2}\''
    cmd = 'sensors | awk \'/temp1/{print "T: " $2}\' | sed "s/+//"' # this removes the +, alternatively use .replace("+", "") on the string
    temp = subprocess.check_output(cmd, shell=True).decode("utf-8").strip()
    #
    cpu_info = CPU + " " + temp

    #mT= MemUsage + " " + temperature

    # Write four lines of text.

    draw.text((x, top + 0), "IP: " + IP, font=font, fill=255)
    #draw.text((x, top + 8), "CPU: " + CPU, font=font, fill=255)
    draw.text((x, top + 8), "CPU: " + cpu_info, font=font, fill=255)
    draw.text((x, top + 16), MemUsage, font=font, fill=255)
    draw.text((x, top + 25), Disk, font=font, fill=255)

    # Display image.
    disp.image(image)
    disp.show()
    time.sleep(0.1)

```


Now everytime the pi restarts it does not work, until I manually start the service. Initially I thought maybe it needs more time before it starts, because the bus is
not yet up, so I added:
```
ExecStartPre=/bin/sleep 30
Type=idle
```

But that also didn't work, So despite the adafruit SSD1306 library using default addresses matching my oled display, I made sure to include the address when creating
the display object (instance...). But that also did not help.

Not really sure what is amiss here and I would appreciate your expertise. It probably is something super silly that I overlooked.

I do have to acknowledge I did have a typo in the oled.service where I mis-spelled "/usr/..." as "usrl/...". that is my dislexic typing,
however I have rectified that and yet it does show in the journal output, despite me fixing that issue (as you can see from the file content above) and issueing the daemon-reload command.

Anyway here is the output from the journalctl -u oled.service
```
sudo journalctl -u oled.service
-- Boot 6992ff21cd7f4cabae5699ab5927b21b --
Apr 08 15:55:42 autobotv2 systemd[1]: Started OLED Display Service.
Apr 08 15:56:52 autobotv2 systemd[1]: Stopping OLED Display Service...
Apr 08 15:56:52 autobotv2 systemd[1]: oled.service: Deactivated successfully.
Apr 08 15:56:52 autobotv2 systemd[1]: Stopped OLED Display Service.
Apr 08 15:56:52 autobotv2 systemd[1]: oled.service: Consumed 17.761s CPU time.
```





Also this:
```
sudo systemctl status oled.service
&#9675; oled.service - OLED Display Service
     Loaded: loaded (/etc/systemd/system/oled.service; disabled; vendor preset: enabled)
     Active: inactive (dead)

```

---

