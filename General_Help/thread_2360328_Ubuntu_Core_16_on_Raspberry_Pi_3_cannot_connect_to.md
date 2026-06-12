---
title: "Ubuntu Core 16 on Raspberry Pi 3 cannot connect to Docker daemon"
date: 2017-05-03
forum: General Help
---

### Post by i-vasiunyk on 2017-05-03
After setting up fresh Ubuntu Core 16 raspberry Pi machine. 
Using image from Ubuntu Core [https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3](https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3).


And installing Docker on it with snap:


    ```
snap install docker
```


I am not able to use docker, as I get an error:
     
    ```
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```


Docker service status is inactive(dead):


    ```
sudo systemctl status snap.docker.dockerd.service
    
    snap.docker.dockerd.service - Service for snap application docker.dockerd
    Loaded: loaded (/etc/systemd/system/snap.docker.dockerd.service; enabled; vendor preset: enabled)
    Active: inactive (dead) (Result: exit-code) since Wed 2017-05-03 10:30:55 UTC; 30min ago
    Process: 1975 ExecStart=/usr/bin/snap run docker.dockerd (code=exited, status=126)
    Main PID: 1975 (code=exited, status=126)


    May 03 10:30:54 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Unit entered failed state.
    May 03 10:30:54 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Failed with result 'exit-code'.
    May 03 10:30:55 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Service hold-off time over, scheduling restart.
    May 03 10:30:55 localhost.localdomain systemd[1]: Stopped Service for snap application docker.dockerd.
    May 03 10:30:55 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Start request repeated too quickly.
    May 03 10:30:55 localhost.localdomain systemd[1]: Failed to start Service for snap application docker.dockerd.

```



Restarting docker service with:


   ```
 sudo systemctl stop snap.docker.dockerd.service
    sudo systemctl start snap.docker.dockerd.service

```

doesn't help.

Is there any additional steps needed to start docker daemon properly?




```
Docker version output:


    Client:
    Version:      1.13.1
    API version:  1.26
    Go version:   go1.7.5
    Git commit:   -snap-a2d8d8c
    Built:        Fri Apr 21 08:56:55 2017
    OS/Arch:      linux/arm
    Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

```

Snap connections for docker:


   ```
 snap interfaces |grep docker
    
    :docker-support           docker:privileged,docker:support
    :firewall-control         docker
    :network                  docker
    :network-bind             docker
    docker:docker-daemon      docker:docker-cli
    -                         docker:account-control
    -                         docker:home



```

Docker service logs


    ```
 sudo journalctl -u snap.docker.dockerd.service -f


     -- Logs begin at Wed 2017-05-03 15:56:02 UTC. --
     May 03 16:12:58 localhost.localdomain systemd[1]: Stopped Service for snap application docker.dockerd.
     May 03 16:12:58 localhost.localdomain systemd[1]: Started Service for snap application docker.dockerd.
     May 03 16:12:59 localhost.localdomain snap[1697]: /snap/docker/91/bin/dockerd-wrapper: 23: /snap/docker/91/bin/dockerd-wrapper: useradd: Permission denied
     May 03 16:12:59 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Main process exited, code=exited, status=126/n/a
     May 03 16:12:59 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Unit entered failed state.
     May 03 16:12:59 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Failed with result 'exit-code'.
     May 03 16:12:59 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Service hold-off time over, scheduling restart.
     May 03 16:12:59 localhost.localdomain systemd[1]: Stopped Service for snap application docker.dockerd.
     May 03 16:12:59 localhost.localdomain systemd[1]: snap.docker.dockerd.service: Start request repeated too quickly.
     May 03 16:12:59 localhost.localdomain systemd[1]: Failed to start Service for snap application docker.dockerd.

```

---

