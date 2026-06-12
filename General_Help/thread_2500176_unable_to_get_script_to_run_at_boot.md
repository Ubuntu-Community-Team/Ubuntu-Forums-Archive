---
title: "unable to get script to run at boot"
date: 2024-08-24
forum: General Help
---

### Post by rebeltaz on 2024-08-24
I am trying to get a script to run at boot up. The command is 

```
sudo python3 weathertv.py
```

I have a bash script in my home directory with 

```

cd /home/derek/
sudo python3 weathertv.py

```

I can run that (or just the single line python) from command and it works fine. I have tried adding one or the other to both the user crontab as well as the root crontab using either

```
@reboot /home/derek/SmartTVWeather.sh
```

-or-

```
@reboot python3 weathertv.py
```


and nothing is working. I have a couple of other scripts that run through the user crontab and I can see them running as 'sh' in the System Monitor, but not this one. When I add the single line python command to the root crontab, I DO see python3 as a running process in System Monitor, but the script itself doens't seem to be doing it's thing. 

Can someone help me figure this out... i.e. tell me what I'm doing wrong? I would really appreciate it.

---

### Post by currentshaft on 2024-08-24
cron doesn't run scripts interactively like you

change cd to pushd or just fully qualify the path to the python file, like python3 /home/derek/weathertv.py (or even just /home/derek/weathertv.py if you include a shebang line in your program).

---

### Post by rebeltaz on 2024-08-24
> **currentshaft said:**
> cron doesn't run scripts interactively like you

change cd to pushd or just fully qualify the path to the python file, like python3 /home/derek/weathertv.py (or even just /home/derek/weathertv.py if you include a shebang line in your program).

This is my current line under 'sudo crontab -e' 

```
 @reboot python3 /home/derek/weathertv.py 
```

I rebooted and, yeah... 'python3' shows as an active process, but it's not running. If I run that same command (without the @reboot, obviously) directly in terminal, it works fine ¯\_(&#12484;)_/¯

I meant to include the full path in my question, because I did have that in there, but missed typing that part in. sorry.

pushcd is good to know about, though.

---

### Post by ian-weisser on 2024-08-25
Does your script require desktop resources (like a $DISPLAY environment variable)?
Desktop resources become available only after login. They won't available to @reboot, which runs earlier.

---

### Post by rebeltaz on 2024-08-25
> **ian-weisser said:**
> Does your script require desktop resources (like a $DISPLAY environment variable)?
Desktop resources become available only after login. They won't available to @reboot, which runs earlier.

I didn't write this, but... I do see some printf commands. Could that be the reason? I can comment those out if it is. I don't really need those.... But would that keep the cript from running at all or would it just not be able to output those line?

```
import requests
import imageio
import time
from datetime import datetime
from io import BytesIO
from PIL import Image
from requests_toolbelt.multipart.encoder import MultipartEncoder

# Configuration
gif_url = "https://radar.weather.gov/ridge/standard/KBMX_loop.gif"
upload_url = "http://192.168.1.165/doUpload"
set_gif_url = "http://192.168.1.165/set"
delete_gif_url = "http://192.168.1.165/delete"
clear_gif_queue_url = "http://192.168.1.165/set?clear=gif"
gif_dir = "/image/80x80.gif"
interval = 60

def clear_gif_queue():
    retries = 3
    for i in range(retries):
        try:
            response = requests.get(clear_gif_queue_url)
            if response.status_code == 200:
                print("GIF queue cleared successfully.")
                return True
            else:
                print(f"Clear GIF queue failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
            print(f"Clear GIF queue failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
    print("Failed to clear GIF queue after multiple attempts")
    return False

def download_and_resize_gif(url, size=(80, 80)):
    retries = 3
    for i in range(retries):
        try:
            response = requests.get(url)
            response.raise_for_status()
            gif = imageio.mimread(BytesIO(response.content), memtest=False)
            resized_gif = [Image.fromarray(frame).resize(size, Image.LANCZOS) for frame in gif]
            output = BytesIO()
            imageio.mimsave(output, resized_gif, format='GIF')
            output.seek(0)
            return output
        except requests.exceptions.RequestException as e:
            print(f"Download retrying.")
            time.sleep(2 ** i)
    raise Exception("Failed to download and resize GIF after multiple attempts")

def upload_gif(gif_data, filename):
    retries = 3
    for i in range(retries):
        try:
            gif_data.seek(0)
            m = MultipartEncoder(fields={'dir': gif_dir, 'image': (filename, gif_data, 'image/gif')})
            response = requests.post(upload_url, data=m, headers={'Content-Type': m.content_type})
            if response.status_code == 200:
                print(f"Upload successful: {filename}")
                return True
            else:
                print(f"Upload retrying")
        except requests.exceptions.RequestException as e:
            print(f"Upload retrying")
            time.sleep(2 ** i)
    print("Failed to upload GIF after multiple attempts")
    return False

def set_gif(filename):
    retries = 3
    for i in range(retries):
        try:
            url = f"{set_gif_url}?gif=/image/80x80.gif/{filename}"
            print(f"Setting GIF with URL: {url}")
            response = requests.get(url)
            if response.status_code == 200:
                print(f"Set GIF successful: {filename}")
                return True
            else:
                print(f"Set GIF failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
            print(f"Set GIF failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
    print("Failed to set GIF after multiple attempts")
    return False

def delete_old_gif(filename):
    retries = 3
    for i in range(retries):
        try:
            url = f"{delete_gif_url}?file=/image/80x80.gif/{filename}"
            print(f"Deleting old GIF with URL: {url}")
            response = requests.get(url)
            if response.status_code == 200:
                print(f"Deleted old GIF successful: {filename}")
                return True
            else:
                print(f"Delete old GIF failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
            print(f"Delete old GIF failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
    print("Failed to delete old GIF after multiple attempts")
    return False

def main():
    if not clear_gif_queue():
        print("Failed to clear GIF queue at startup.")
        return

    last_filename = None
    while True:
        try:
            # Step 1: Download and resize the GIF
            gif_file = download_and_resize_gif(gif_url)
            filename = datetime.now().strftime("weather%H%M.gif")
            
            # Step 2: Upload the resized GIF
            if not upload_gif(gif_file, filename):
                continue
            
            # Step 3: Set the uploaded GIF
            if not set_gif(filename):
                continue

            # Step 4: Delete the old GIF
            if last_filename and not delete_old_gif(last_filename):
                continue
            
            last_filename = filename

            time.sleep(interval)
        except Exception as e:
            print("An error occurred:", e)
            time.sleep(interval)

if __name__ == "__main__":
    main()
```

---

### Post by currentshaft on 2024-08-25
It might be failing because it runs before networking is up.

I would make this a systemd service that depends on networking being up, rather than a cron

---

### Post by rebeltaz on 2024-08-25
> **currentshaft said:**
> It might be failing because it runs before networking is up.

I would make this a systemd service that depends on networking being up, rather than a cron

That is a new one to me, so I had to do some searching to figure out how. Here's what I did. 

I removed the @reboot entry from sudo crontab. Then I modified the script to be silent by commenting out the print statements, calling it weathertv_silent.py

```
import requests
import imageio
import time
from datetime import datetime
from io import BytesIO
from PIL import Image
from requests_toolbelt.multipart.encoder import MultipartEncoder

# Configuration
gif_url = "https://radar.weather.gov/ridge/standard/KBMX_loop.gif"
upload_url = "http://192.168.1.165/doUpload"
set_gif_url = "http://192.168.1.165/set"
delete_gif_url = "http://192.168.1.165/delete"
clear_gif_queue_url = "http://192.168.1.165/set?clear=gif"
gif_dir = "/image/80x80.gif"
interval = 60

def clear_gif_queue():
    retries = 3
    for i in range(retries):
        try:
            response = requests.get(clear_gif_queue_url)
            if response.status_code == 200:
#                print("GIF queue cleared successfully.")
                return True
            else:
#                print(f"Clear GIF queue failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
#            print(f"Clear GIF queue failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
#    print("Failed to clear GIF queue after multiple attempts")
    return False

def download_and_resize_gif(url, size=(80, 80)):
    retries = 3
    for i in range(retries):
        try:
            response = requests.get(url)
            response.raise_for_status()
            gif = imageio.mimread(BytesIO(response.content), memtest=False)
            resized_gif = [Image.fromarray(frame).resize(size, Image.LANCZOS) for frame in gif]
            output = BytesIO()
            imageio.mimsave(output, resized_gif, format='GIF')
            output.seek(0)
            return output
        except requests.exceptions.RequestException as e:
#            print(f"Download retrying.")
            time.sleep(2 ** i)
    raise Exception("Failed to download and resize GIF after multiple attempts")

def upload_gif(gif_data, filename):
    retries = 3
    for i in range(retries):
        try:
            gif_data.seek(0)
            m = MultipartEncoder(fields={'dir': gif_dir, 'image': (filename, gif_data, 'image/gif')})
            response = requests.post(upload_url, data=m, headers={'Content-Type': m.content_type})
            if response.status_code == 200:
#                print(f"Upload successful: {filename}")
                return True
            else:
#                print(f"Upload retrying")
        except requests.exceptions.RequestException as e:
#            print(f"Upload retrying")
            time.sleep(2 ** i)
#    print("Failed to upload GIF after multiple attempts")
    return False

def set_gif(filename):
    retries = 3
    for i in range(retries):
        try:
            url = f"{set_gif_url}?gif=/image/80x80.gif/{filename}"
#            print(f"Setting GIF with URL: {url}")
            response = requests.get(url)
            if response.status_code == 200:
#                print(f"Set GIF successful: {filename}")
                return True
            else:
#                print(f"Set GIF failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
#            print(f"Set GIF failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
#    print("Failed to set GIF after multiple attempts")
    return False

def delete_old_gif(filename):
    retries = 3
    for i in range(retries):
        try:
            url = f"{delete_gif_url}?file=/image/80x80.gif/{filename}"
#            print(f"Deleting old GIF with URL: {url}")
            response = requests.get(url)
            if response.status_code == 200:
#                print(f"Deleted old GIF successful: {filename}")
                return True
            else:
#                print(f"Delete old GIF failed: {response.status_code} {response.text}")
        except requests.exceptions.RequestException as e:
#            print(f"Delete old GIF failed: {e}, retrying ({i + 1}/{retries})...")
            time.sleep(2 ** i)
#    print("Failed to delete old GIF after multiple attempts")
    return False

def main():
    if not clear_gif_queue():
#        print("Failed to clear GIF queue at startup.")
        return

    last_filename = None
    while True:
        try:
            # Step 1: Download and resize the GIF
            gif_file = download_and_resize_gif(gif_url)
            filename = datetime.now().strftime("weather%H%M.gif")
            
            # Step 2: Upload the resized GIF
            if not upload_gif(gif_file, filename):
                continue
            
            # Step 3: Set the uploaded GIF
            if not set_gif(filename):
                continue

            # Step 4: Delete the old GIF
            if last_filename and not delete_old_gif(last_filename):
                continue
            
            last_filename = filename

            time.sleep(interval)
        except Exception as e:
#            print("An error occurred:", e)
            time.sleep(interval)

if __name__ == "__main__":
    main()
```

Then, going by this page here - [https://linuxhandbook.com/create-systemd-services/](https://linuxhandbook.com/create-systemd-services/) - I create a file called weathertv_update.service containing

```
[Unit]
Description=update SmartTVPro Weather animated gif
After=multi-user.target

[Service]
ExecStart=/usr/bin/python3 /home/derek/weathertv_silent.py
Type=exec

[Install]
WantedBy=multi-user.target
```

that I copy to the /etc/systemd/system directory. I then run 

```
sudo systemctl daemon-reload
sudo systemctl enable weathertv_update.service
```

and then rebooted. As before, python3 is showing as a process in the System Monitor, but the SmartTV device is not being updated, unless/until I manually run the python script from the command line. 

I've never done a service before, so if I did that wrong....

---

### Post by ian-weisser on 2024-08-25
Remove the line "After=multi-user.target"

---

### Post by rebeltaz on 2024-08-25
> **ian-weisser said:**
> Remove the line "After=multi-user.target"

I tend to be an idiot. The python3 in System Monitor has nothing to do with this. Some gnome-tweak thing. 

ANYWAY...

I removed that line from the .service and rebooted. It still didn't work, so I figured out how to see the error log for the services

```
journalctl -u weathertv_update.service -b
```

That told me that the script had the wrong indentation on line 28. I figured it had to do with the print statements I just commented out. I remember reading tonight that any output from a running service was just sent to a null device, so I decided to try just using the original weathertv.py script as it was, print statements and all. 

I rebooted again and it still didn't work, but.... running the journalctl command again, I can see that I'm getting there. It is actually running, but since the network isn't fully up and connected to the internet yet, it's not able to grab the image it needs. No big deal. It should try again every hour. 

Except.... 

```

Aug 25 21:12:10 laptop systemd[1]: Starting update SmartTVPro Weather animated gif...
Aug 25 21:12:10 laptop systemd[1]: Started update SmartTVPro Weather animated gif.
Aug 25 21:12:18 laptop python3[773]: Clear GIF queue failed: HTTPConnectionPool(host='192.168.1.165', port=80): Max retries exceeded with url: /set?clear=gi>
Aug 25 21:12:18 laptop python3[773]: Clear GIF queue failed: HTTPConnectionPool(host='192.168.1.165', port=80): Max retries exceeded with url: /set?clear=gi>
Aug 25 21:12:18 laptop python3[773]: Clear GIF queue failed: HTTPConnectionPool(host='192.168.1.165', port=80): Max retries exceeded with url: /set?clear=gi>
Aug 25 21:12:18 laptop python3[773]: Failed to clear GIF queue after multiple attempts
Aug 25 21:12:18 laptop python3[773]: Failed to clear GIF queue at startup.
Aug 25 21:12:18 laptop systemd[1]: weathertv_update.service: Deactivated successfully.

```

That last line has me bothered. It says that the service has been deactivated successfully. But I don't WANT it to deactivate, successfully or otherwise! 

I've figured out WHY it was deactivated, though. The script is written in such a way that it breaks if any action fails, rather than just retrying. I'll have to try and fix that. I am also going to have to restructure it so I can get rid of the print statements without breaking it. As verbose as that it, it's going to fill a log file quickly. 

THANK YOU ALL FOR ALL OF YOUR HELP!

---

