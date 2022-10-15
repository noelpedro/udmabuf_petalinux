# udmabuf_petalinux

Clone the udmabuf git repo:


`$: git clone https://github.com/ikwzm/udmabuf`

Enable the module in petalinux project with: 


`$: petalinux-create -t mudules -n u-dma-buf --enable` 

Copy the kernel module source code over to newly enabled u-dma-buf module with: 


`$: cp udmabuf/u-dma-buf.c project-spec/meta-user/recepies-modules/u-dma-buf/files/`



Build the petalinux Project 



copy over the kernel object to device 


`$: scp <PETALINUX_PROJECT_ROOT>/build/tmp/sysroots-components/plnx-components/u-dma-buf/lib/modules/<KERNEL_build_VERSION>/extra/u-dma-buf.ko <DEVICE>` 


If there is no /lib/modules folder in device then for the above recursively secure copy the modules folder to device and move it to /lib. 


Make sure the .ko file above is moved to the path `/lib/modules/<KERNEL_build_VERSION>/extra/u-dma-buf` 



Now as root append to the file `/etc/modules` the string `u-dma-buf` 



Lastly run `sudo depmod -a` and reboot



