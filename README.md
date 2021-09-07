# i96

Documentation and apps for the OrangePi-i96 board. Fixes the GPIO access, and includes notes to help make the board more useable.

See the [wiki](http://alt.pbeirne.com:3000/patb/i96/wiki) for the documentation.

Download the `gpio_fixup.py` file onto your OrangePi-i96. I usually install it into `/usr/local/bin'.

``` 
sudo -i                  # change to root
cd /usr/local/bin
wget http://wiki.pbeirne.com/patb/i96/raw/master/gpio_fixup.py

# add a line to /etc/rc.local to execute this at startup
sed -i "/^exit 0$/i\/usr/local/bin/gpio_fixup.py" /etc/rc.local
```

That little script will run at boot time, and change the gpio pins on the 40 pin connector (pins 23-34) into true GPIO pins, and it'll restore proper operation of the UART2 and SPI2 pins (pins 3,9,8,10,12,14) **NOTE: this is OrangePi-i96 specific; do not use on the 2G-iot board**

`gpio_fixup.sh` is the equivalent script written in bash, using `devmem2` to access the cpu registers.

`devmem2.py` is a local version of the program to access the cpu registers. Use if you can't download `devmem2` from the Debian/Ubuntu repositories. `devmem2.py` uses Python3 and is very slow, and must be run by root or sudo.

`blink.py` is just an example to show how you might play with the GPIO lines.
