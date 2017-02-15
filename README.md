# linux-gpio-nct5104d
NCT5104D GPIO Linux Driver

<b>Preconditions (Compile):</b><br>
you should have the following packages installed:
* linux-headers-$(uname -r)
* build-essential
* make
* git (you can also download the repo as zip)

`apt-get install -y linux-headers-$(uname -r) build-essential make git`

`git clone <this repo url>`

<b>Compile:</b><br>
run `make` in the driver folder on the target machine<br>
(otherwise your driver gets compiled for a different kernal version)

<b>Load the driver:</b><br>
`insmod gpio-nct5104d.ko`

<b>Unload the driver:</b><br>
unexport all the used GPIO Pins first, then run<br>
`rmmod gpio-nct5104d.ko`

<b>Export a GPIO Pin:</b><br>
`echo 0 > /sys/class/gpio/export` will export/reserve/setup the gpio pin 0

<b>Unexport a GPIO Pin:</b><br>
`echo 0 > /sys/class/gpio/unexport` will unexport/free the gpio pin 0

<b>Set GPIO Pin as output:</b><br>
`echo out > /sys/class/gpio/gpio0/direction`

<b>Set GPIO Pin output value:</b><br>
`echo 1 > /sys/class/gpio/gpio0/value`

<b>Read GPIO Pin value:</b><br>
`cat /sys/class/gpio/gpio0/value`

<b>Invert GPIO Pin logic:</b><br>
`echo 1 > /sys/class/gpio/gpio0/active_low`

<b>Using the Kernel interrupt system for GPIO Pins:</b><br>
`echo <TRIGGER_TYPE> >/sys/class/gpio/gpio0/edge`<br>
`TRIGGER_TYPE` can be one of the following values:
* none
* falling
* rising
* both

<b>Show GPIO states using kernal debug information:</b><br>
`cat /sys/kernel/debug/gpio`<br>
this has to be enabled in your kernal

<b>Additional informatio:</b><br>
see those pages for some c-code examples:<br>
http://wiki.gnublin.org/index.php/GPIO<br>
http://falsinsoft.blogspot.de/2012/11/access-gpio-from-linux-user-space.html<br>

see the Kernel documentation for more details:<br>
https://www.kernel.org/doc/Documentation/gpio/sysfs.txt<br>
https://www.kernel.org/doc/Documentation/gpio/gpio-legacy.txt<br>
and so on...
