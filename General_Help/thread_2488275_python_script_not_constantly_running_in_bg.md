---
title: "python script not constantly running in bg"
date: 2023-06-29
forum: General Help
---

### Post by sniper8752 on 2023-06-29
I have a python3 script to constantly run in the background to monitor a service.  But it seems that it is not constantly running, as the service is monitors, is not restarted when broken.  Here's my script and my crontab entry:

```
import timeimport subprocess


log_file_path = "/var/log/syslog"
search_phrases = ["Driver not connected", "Data stale"]
check_interval = 30  # in seconds


def check_log_for_errors(log_file_path, search_phrases):
    with open(log_file_path, "r") as file:
        lines = file.readlines()
        if lines:
            last_log_entry = lines[-1].strip()
            if any(phrase in last_log_entry for phrase in search_phrases):
                print("Error message found:", last_log_entry)
                run_upsdrvctl()


def run_upsdrvctl():
    try:
        subprocess.run(["upsdrvctl", "start"], check=True)
        print("upsdrvctl executed successfully.")
    except subprocess.CalledProcessError as e:
        print("Error executing upsdrvctl:", e)


while True:
    check_log_for_errors(log_file_path, search_phrases)
    time.sleep(check_interval)

```

Crontab entry:
```
@reboot python3 /home/user/check-stale-data-v3.py
```

---

### Post by Holger_Gehrke on 2023-06-29
Kind of obvious: you're only checking the log every 30 seconds on whether the last line in the log contains your search phrases. But you're checking the syslog and everything writes to that. Chances are close to certainty that something else will have written the last entry. If you can find out the pid of the process you're monitoring you could simply check on whether or not the process still exists. Or if the process writes to the journal you could use the module systemd.journal and filter to only get messages from the interesting program.

Holger

---

