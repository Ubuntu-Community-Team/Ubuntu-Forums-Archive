---
title: "decreasing volume sensitivity of bluetooth headset's microphone in Ubuntu 18.04?"
date: 2021-03-09
forum: General Help
---

### Post by thosecars822 on 2021-03-09
Hello

I would like to know how I can decrease the sensitivity of the microphone of a bluetooth headset effectively in Ubuntu 18.04.

There is a volume setting for the headset's microphone and I can turn it up or down. Nonetheless, regardless of how high it is, as long as it is not zero, the headset's microphone sensitivity seems to be the same.

I would like to decrease the sensitivity of the microphone to prevent environment noise from getting recorded but so far it seems the microphone sensitivity is always the same, regardless of the position of the correspobnding volume slide bar.
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARoAAAAbCAYAAACjmECrAAACd0lEQVR4Ae2c3XGDMBAG04JboAW1QAu0QAu0QAtuwS3QAi3QAi0o88EowUR5MdyNsfaBkRExEqfVcvw4XyGEyEIMYAAGLBn4stw5 wZeGIABMYBoyOjIaGHAnAFEA2TmkJHVkNUgGkSDaGDAnAFEA2TmkJHRkNEgGkSDaGDAnAFX0TRNE8dxjPM8x3EcotY523G2g4HPZ8BVNJKLJJOWcRhcRVPXIXZdG/u XxZ9Vh2gEwMYsGXAVTRJMNvSa4C7rovTNP1ILvVBddrm1Q/asQWa L5nfIsQjTKYJJb/Sv0NkL4npIzL9cfFRTTKGgRLbpKrPm23AKptmmy7ub5wz j6QFswxD6Pc EiGk1qDVZucqd6i8HsQxWnxz3bbq4vj8c9VlXFQgxg4ImB2xKPI3P0Y0XThioO4RbnzH2ZnGRUZ5lZHRkkvnv8jEoMj8VQJ AjMXQTjZ7u5CZ4qj9yELnvdqGKY33LtpnrR6rL7Yu6Y5ASv vHbxXN67JxEc00jbFtm6jH2WlCqxyG9V0abT8bRjKa68N9NhPs73UmLpHR6InOKpV6KX8ls65bPfHhHg33m7jndgYDF7lHo8sjiUaLMpu6rpcy1Vm NMdTp9fPYmQAxO4sBlwundRZyWT/PovWLSWTgrRvd3v5lj5bZVWpD5RM2pIZcBNNCnKa2CpTnUfJm8FMdA/OaCPPmYto9r9x2spGn7XdY4CUPXXt5rdOLb918og7beQnX0lxcRHNXiy59ZKCzrEy8UpjwEU0pQWV40UkMPDMAKLhnx65XLYy8Z4nXmnxQDSIBtHAgDkDiAbIzCEr7ezN8f7N3hANokE0MGDOwDc66M9 nW8LrAAAAABJRU5ErkJggg==[/IMG]

That means, the volume setting is above zero but it is almost zero and the microphone seems to have the same sensitivity as if I had selected the maximum volume. This does not happen with the computer's internal microphone. That means, I can change the sensitivity of the computer internal microphone effectively by changing the position of the corresponding slide bar.
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARQAAAAfCAYAAAAmwDIOAAACmUlEQVR4Ae2b7ZGDIBBA00JaSAu0QAu2YAu0YAvXgi3YAi3Ygi3szZojw2TQ LHORO/9YFR0DIHHY0G9OeeERB3AAAxYMHCzuAn3AEYYgAFlAKEQoRGhwoAZAwgFmMxgIkohSkEoCAWhwIAZAwgFmMxgIkIhQkEoCAWhwIAZAwgFmMxgIkIhQkEoCAWhwIAZAwgFmMxgIkIhQjERSlVVEmOUYRgkxk70GLiACwb HwMmQlGJqExSil2HUIh8YOBLGPDeSQi1NE0zJt3XvCOEbyKUJJJ8e0RhuecxEFCv163XEIL0ff8a7FMf1Tw9Z932COVLRhHrhuV 15XE0rbViCQJZGqr1yy935LrdglFLac/Uiqs5qfzSwqy9hrvnFQk6gAGigyEqir2y1JftVzz3CUULdycUNL5tbL4dH3jHtK5u3SeRB3AQImBvv1ZLJS2bc2ilNMJpf6TSe/vQqIOYKDMwFBYNylFJ5pnOZPYLRRdLS4VNOV/ijbWng/uIRGZIFMYmGWg1Cfn8tb2w6nrdwml76PUdSX6mDgvbNc930XR81M/vDWfCKU8IjFSUy85A6eMUHSF CkPP25VKvmx9QpyktBrDYV1FNaRWEcrMnDKNRSd1qhANGmk4r0ftynvqJdnVCw85eEpF0/5phk45VOesWN7N759l095NDI5UiYpUmHLuxYwMM2A9sO8X5b2rWcRu9ZQ8sbMC5vnsz/d4NQNdXM0A6d6U/b9G55cKrqv54 uMO5Pp4SBeQZ0thDq7Fue ku/5XkXSOmYxp5vbOqH rkSA2ZTnitVCv FTg4D2xhAKHwcyLQUBswYQCjAZAYTo/q2Uf1K9YZQEApCgQEzBhAKMJnBdKWRlv yLdpCKAgFocCAGQO/RnVTAnMshdQAAAAASUVORK5CYII=[/IMG]

Does anyone know how could I decrease the sensitivity of the bluetooth headset's microphone effectively in Ubuntu 18.04 and prevent so environment noises from getting picked up?

I have run ```
pactl load-module module-loopback
``` in case that matters.


Thanks in advance

---

