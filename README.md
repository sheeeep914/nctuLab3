# Route Configuration

This repository is a lab for NCTU course "Introduction to Computer Networks 2018".

---
## Abstract

In this lab, we are going to write a Python program with Ryu SDN framework to build a simple software-defined network and compare the different between two forwarding rules.

---
## Objectives

1. Learn how to build a simple software-defined networking with Ryu SDN framework
2. Learn how to add forwarding rule into each OpenFlow switch

---
## Execution

> TODO:
> * How to run your program?  
   1. 打開終端機，用ssh登入我的container  
   2. cd到 /root/Route_Configuration/src/ 這個資料夾  
      `cd /root/Route_Configuration/src/`  
   3. 開兩個terminal頁面 
   4. 第一個頁面運行topo.py  
      `mn --custom topo.py --topo topo --link tc --controller remote`  
   5. 第二個頁面第一次運行SimpleController.py  
      `ryu-manager SimpleController.py –observe-links`  
   6. 在第一個頁面下iperf   
> * What is the meaning of the executing command (both Mininet and Ryu controller)?
> * Show the screenshot of using iPerf command in Mininet (both `SimpleController.py` and `controller.py`)

---
## Description

### Tasks

> TODO:
> * Describe how you finish this work in detail

1. Environment Setup
   1) 加入GitHub Classroom  
   2) 打開終端機，用ssh登入我的container
      ```
      ssh -p 16328 root@140.113.195.69
      Password: cn2018
      ```
   3) 把lab3的資料clone下來  
      `git clone https://github.com/nctucn/lab3-sheeeep914.git Route_Configuration`  
   4) 把Mininet開起來，測試用  
      `sudo mn`  
      
2. Example of Ryu SDN  
   1) 登入container，進到src資料夾，讓SimpleTopo.py跑起來(by Mininet)  
   ```
   cd /root/Route_Configuration/src/  
   mn --custom SimpleTopo.py --topo topo --link tc --controller remote  
   ```
   2) 再開另一個terminal，進到src資料夾，讓SimpleController.py跑起來  
   ```
   cd /root/Route_Configuration/src/  
   ryu-manager SimpleController.py --observe-links  
   ```
   3) 這樣就等於跑起來了 可以在第一個terminal裡輸入 h1 ping h2 來測試連線是否建立成功  
3. Mininet Topology  
   1) 先複製一份SimpleTolo.py 並命名為topo.py 一樣放在src資料夾裡面  
   ```
   #確定路徑是在/root/Route_Configuration/src/  
   cp SimpleTopo.py topo.py
   ```
   2) 將s1,s2,s3的bandwidth,delay,loss都加進topo.py裡  
   3) 先把topo.py運行起來(by Mininet)  
   `mn --custom topo.py --topo topo --link tc --controller remote`  
   4) 再開另一個terminal，進到src資料夾，讓SimpleController.py跑起來  
   ```
   cd /root/Route_Configuration/src/  
   ryu-manager SimpleController.py --observe-links  
   ```
   
4. Ryu Controller

5. Measurement

### Discussion

> TODO:
> * Answer the following questions

1. Describe the difference between packet-in and packet-out in detail.
   
2. What is “table-miss” in SDN?
   
3. Why is "`(app_manager.RyuApp)`" adding after the declaration of class in `controller.py`?
   
4. Explain the following code in `controller.py`.
    ```python
    @set_ev_cls(ofp_event.EventOFPPacketIn, CONFIG_DISPATCHER)
    ```

5. What is the meaning of “datapath” in `controller.py`?
   
6. Why need to set "`ip_proto=17`" in the flow entry?
   
7. Compare the differences between the iPerf results of `SimpleController.py` and `controller.py` in detail.
   
8. Which forwarding rule is better? Why?

---
## References

> TODO: 
> * Please add your references in the following

* **Ryu SDN**
    * [Ryubook Documentation](https://osrg.github.io/ryu-book/en/html/)
    * [Ryubook [PDF]](https://osrg.github.io/ryu-book/en/Ryubook.pdf)
    * [Ryu 4.30 Documentation](https://github.com/mininet/mininet/wiki/Introduction-to-Mininet)
    * [Ryu Controller Tutorial](http://sdnhub.org/tutorials/ryu/)
    * [OpenFlow 1.3 Switch Specification](https://www.opennetworking.org/wp-content/uploads/2014/10/openflow-spec-v1.3.0.pdf)
    * [Ryubook 說明文件](https://osrg.github.io/ryu-book/zh_tw/html/)
    * [GitHub - Ryu Controller 教學專案](https://github.com/OSE-Lab/Learning-SDN/blob/master/Controller/Ryu/README.md)
    * [Ryu SDN 指南 – Pengfei Ni](https://feisky.gitbooks.io/sdn/sdn/ryu.html)
    * [OpenFlow 通訊協定](https://osrg.github.io/ryu-book/zh_tw/html/openflow_protocol.html)
* **Python**
    * [Python 2.7.15 Standard Library](https://docs.python.org/2/library/index.html)
    * [Python Tutorial - Tutorialspoint](https://www.tutorialspoint.com/python/)
* **Others**
    * [Cheat Sheet of Markdown Syntax](https://www.markdownguide.org/cheat-sheet)
    * [Vim Tutorial – Tutorialspoint](https://www.tutorialspoint.com/vim/index.htm)
    * [鳥哥的 Linux 私房菜 – 第九章、vim 程式編輯器](http://linux.vbird.org/linux_basic/0310vi.php)

---
## Contributors

> TODO:
> * Please replace "`YOUR_NAME`" and "`YOUR_GITHUB_LINK`" into yours

* [楊郁欣](https://github.com/sheeeep914)
* [David Lu](https://github.com/yungshenglu)

---
## License

GNU GENERAL PUBLIC LICENSE Version 3
