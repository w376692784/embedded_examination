# 概念
## 嵌入式系统的定义？
    以应用为中心、以计算机技术为基础、软硬件可裁剪、适应应用系统对功能、可靠性、成本、体积、功耗严格要求的专用计算机系统.

## 嵌入式系统的软、硬件组成？
    嵌入式硬件系统
        嵌入式处理器
        各种类型存储器
        模拟电路及电源
        接口控制器及接插件
##
    嵌入式软件系统
        实时操作系统（RTOS）
        板级支持包（BSP）
        设备驱动（Device Driver）
        协议栈（Protocol Stack）
        应用程序（Application）

## 处理器及操作系统的选型主要考虑哪些方面？
    功能、可靠性、成本、体积、功耗
###
    处理器选择要考虑的主要因素有：
    ① 处理器的性能 
    ② 处理器的技术指标。 
    ③ 功耗。
    ④ 软件支持工具。
    ⑤ 处理器是否内置调试工具。
    ⑥ 供应商是否提供评估板。
    ⑦ 其它因素：生产规模、开发市场的目标、软件对硬件的依赖性。
###
    操作系统的选择需要考虑到以下几个方面：
    ① 操作系统本身所提供的开发工具。
    ② 操作系统向硬件接口移植的难度。
    ③ 操作系统的内存要求。
    ④ 开发人员是否熟悉此操作系统及其提供的系统API。
    ⑤ 操作系统是否提供硬件的驱动程序，如网卡驱动程序等。
    ⑥ 操作系统的是否具有可剪裁性。
    ⑦ 操作系统的实时性能。
###
    编程语言的选择主要考虑以下因素：
    ① 通用性。
    ② 可移植性程度。
    ③ 执行效率。
    ④ 可维护性。

## 交叉开发、交叉开发环境？为何需要交叉开发环境？
### 交叉开发:
    在一台通用计算机上进行软件的编辑编译，然后下载到嵌入式设备中运行调试的开发方式。
### 交叉开发环境
    交叉开发环境是指用于嵌入式软件开发的所有工具软件的集合,交叉开发环境由宿主机和目标机组成，宿主机与目标机之间在物理连接的基础上建立起逻辑连接。
### 为何需要
    由于其本身不具备自主开发能力，即使设计完成以后，用户通常也是不能对其中的程序功能进行修改，必须有一套开发工具和环境才能进行开发。
## 嵌入式交叉开发环境的主要组成？
        文本编辑器
        交叉编译器
        交叉调试器
        仿真器
        下载器等
## 嵌入式Linux 开发主要流程？
    建立开发环境
    配置开发主机
    建立引导装载程序BOOTLOADER
    下载别人已经移植好的LINUX 操作系统
    建立根文件系统
    建立应用程序的flash 磁盘分区
    开发应用程序

## 构建嵌入式linux交叉开发环境的主要方法？
    手动编译
    用脚本编译
    下载编译好的二进制文件
#
## 嵌入式linux系统的软件的主要组成？及对应的主要开发工作？

#

## 嵌入式系统与PC之间的区别
    嵌入式系统一般是专用系统，而PC是通用计算平台
    嵌入式系统的资源比PC少得多
    嵌入式系统软件故障带来的后果比PC机大得多
    嵌入式系统一般采用实时操作系统
    嵌入式系统大都有成本、功耗的要求
    嵌入式系统得到多种微处理器体系的支持
    嵌入式系统需要专用的开发工具

## 嵌入式系统与单片机的区别
    目前嵌入式系统的主流是以32位嵌入式微处理器为核心的硬件设计和基于实时操作系统（RTOS）的软件设计
    单片机系统多为4位、8位、16位机，不适合运行操作系统，难以进行复杂的运算及处理功能
    嵌入式系统强调基于平台的设计、软硬件协同设计，单片机大多采用软硬件流水设计
    嵌入式系统设计的核心是软件设计（占70%左右的工作量），单片机系统软硬件设计所占比例基本相同

## 嵌入式系统的几个重要特征
    操作系统内核小
    专用性强
    系统精简
    高实时性OS
    嵌入式软件开发走向标准化
    嵌入式系统开发需要开发工具和环境


# ARM
## ARM硬件电路最小系统组成？
    MCU,RAM,ROM,FLASH,电源,时钟,复位
    JTAG调试接口
## ARM处理器的主要工作模式？
![工作模式](./图/4.png)
## 核心寄存器的作用：
    R13,R14,pc,cpsr,spsr
##
    R0 到 R15 可以直接访问
    R0 到 R12 是通用寄存器
##
    R13: 堆栈指针 (sp) (通常)
    每种处理器模式都有单独的堆栈,在用户应用程序的初始化部分，一般都要初始化每种模式下的R13，使其指向该运行模式的栈空间 
    Thumb中，某些指令强制性的要求使用R13作为堆栈指针 
##
    R14:子程序链接寄存器（Subroutine Link Register）或链接寄存器LR
    当执行BL子程序调用指令时，R14←R15（程序计数器PC）。
    其他情况下，R14用作通用寄存器。
    与之类似，当发生中断或异常时，对应的分组寄存器R14_svc、R14_irq、R14_fiq、R14_abt和R14_und用来保存R15的返回值。 
##
    R14为链接寄存器（LR），在结构上有两个特殊功能：
    在每种模式下，模式自身的R14版本用于保存子程序返回地址；
    当发生异常时，将R14对应的异常模式版本设置为异常返回地址（有些异常有一个小的固定偏移量）。
##
    R15 程序计数器 (PC)
    在ARM状态下，位[1:0]为0 ，在Thumb状态下，位[0]为0 。
    R15虽然也可用作通用寄存器，但一般不这么使用，否则程序的执行结果可能未知。
    对于R15的使用一定要慎重。当向R15中写入一个地址值时，程序将跳转到该地址执行。由于在ARM状态下指令总是是字对齐的，所以R15值的第0位和第1位总为0，PC［31：2］用于保存地址。
    由于ARM体系结构采用了多级流水线技术，对于ARM指令集而言，PC总是指向当前指令的下两条指令的地址，即PC的值为当前指令的地址值加8个字节。 
##
    CPSR – Current Program Status Register，当前程序状态寄存器
    CPSR可在任何运行模式下被访问，它包括条件标志位、中断禁止位、当前处理器模式标志位，以及其他一些相关的控制和状态位。
##
    5个SPSRs-- Saved  Program Status Register 程序状态保存寄存器 当异常发生时保存CPSR状态
    当异常发生时，SPSR用于保存CPSR的当前值，从异常退出时则可由SPSR来恢复CPSR。
    由于用户模式和系统模式不属于异常模式，他们没有SPSR，当在这两种模式下访问SPSR，结果是未知的。

## ARM处理器的启动程序设计？


## 异常处理
    当正常的程序执行流程发生暂时的停止时，称之为异常，例如处理一个外部的中断请求。在处理异常之前，当前处理器的状态必须保留，这样当异常处理完成之后，当前程序可以继续执行。处理器允许多个异常同时发生，它们将会按固定的优先级进行处理。
    异常类型
        FIQ 
        IRQ(Interrupt ReQuest)
        未定义指令
        预取中止
        数据中止
        复位
        软件中断Software interrupt

### 异常向量及异常向量表
#### 异常向量
    当一种异常发生的时候，ARM处理器会跳转到对应该异常的固定地址去执行异常处理程序，而这个固定的地址，就称之为异常向量。
#### 异常向量表
    由异常向量及其处理函数跳转关系组成的表即为异常向量表.

### arm处理器的异常处理流程（重点是响应与返回）
#### 响应
    1、在相应的链接寄存器LR (r14)中保存下一条指令的地址，以便程序在处理异常返回时能从正确的位置重新开始行 
    2、将CPSR复制到相应的SPSR中
    3、根据异常类型，强制设置CPSR的运行模式位 
    4、强制PC从相关的异常向量地址取下一条指令执行，从而跳转到相应的异常处理程序处。
#### 异常处理
    •保存断点
    – 在相应的链接寄存器LR (r14)中保存下一条指令的地址，以便程序在处理异常返回时能从正确的位置重新开始执行
    •保存现场
    – 将CPSR复制到相应的SPSR中
    •设置工作模式
    – 根据异常类型，强制设置CPSR的运行模式位
    •转向异常处理程序
    – 强制PC从相关的异常向量地址取下一条指令执行，从而跳转到相应的异常处理程序处。
    •如果异常发生时处于Thumb状态，则当异常向量地址加载
    入PC时，处理器自动切换到ARM 状态。
#### 返回
    将LR寄存器中的值减去相应的偏移量送到PC中(The offset will vary depending on the type of exception)
    将 SPSR 复制回 CPSR
    清除禁止中断标志,如果它被设置成使能
    所有修改过的用户寄存器必须从处理程序的保护堆栈中恢复（即出栈）。
    可以认为程序总是从复位异常处理程序开始执行的，因此复位异常处理程序不需要返回。
#### 指令实例
    STMFD  R13!，{R0，R4-R12，LR}	 ；将寄存器列表中的寄存器R0，R4到R12，LR存入堆栈。
    LDMFD R13!,{R0，R4-R12，PC} ∧ ；将堆栈内容恢复到寄存器R0，R4到R12，PC，同时SPSR复制到CPSR 
    {∧}为可选后缀，当指令为LDM且寄存器列表中包含R15，选用该后缀时表示：除了正常的数据传送之外，还将SPSR复制到CPSR。


### 对中断嵌套的处理
#
    指令示例：
    STMFD  R13!，{R0，R4-R12，LR}	 
    LDMFD  R13!，{R0，R4-R12，PC}
    LDMFD R13!,{R0，R4-R12，PC} ∧    ；
    注意条件执行相关代码
    分析startup.s相关代码
![代码段](./图/1.png)

### 代码指令分析：
    AREA	Init，CODE，READONLY 
        ……
        CODE32		； 通知编译器其后的指令为32位的ARM指令
        LDR	R0，＝NEXT＋1	；将跳转地址放入寄存器R0
        BX	R0	；	 程序跳，并将处理器切换到Thumb工作状态
    ……
        CODE16		；	通知编译器其后的指令为16位的Thumb指令
    NEXT	LDR	R3，＝0x3FF	
        ……
        END					
#
## 高级语言和汇编语言函数间的相互调用 :
### 汇编调用C：
    IMPORT Main			;通知编译器该标号为一个外部标号
    AREA    Init,CODE,READONLY	；定义一个代码段
    ENTRY				；定义程序的入口点
    LDR	R0,=0x3FF0000		；初始化系统配置寄存器
    LDR	R1,=0xE7FFFF80
    STR	R1,[R0]
    LDR	SP,=0x3FE1000		；初始化用户堆栈
    BL	Main			；跳转到Main（）函数处的C/C++代码执行
    END				；标识汇编程序的结束
    以上的程序段完成一些简单的初始化，然后跳转到Main（）函数所标识的
    C/C ＋＋代码处执行主要的任务，此处的Main仅为一个标号，也可使用其他名称。

### 程序代码段的组成分析以及汇编语言的寄存器编程例如：
    标注下面程序各条语句中的含义
    AREA   Init , CODE , READONLY
    ENTRY
    LDR    R0, =0x3ff5000
    LDR    R1, 0x0f
    STR     R1,[R0]
    LDR     R0, =0x3ff5008
    LDR    R1, 0x01
    STR     R1,[R0]
    BL      PROC
    :
    :
    :
    :
    PROC
    :
    :
    MOV    PC,  LR
    :
    :
    END
![代码段](./图/2.png)
![代码段](./图/3.png)

### 汇编语言程序结构
    一个汇编程序至少应该有一个代码段，当程序较长时，可以分割为多个代码段和数据段，多个段在程序编译链接时最终形成一个可执行的映象文件。
    可执行映象文件通常由以下几部分构成：
        一个或多个代码段，代码段的属性为只读。
        零个或多个包含初始化数据的数据段，数据段的属性为可读写。
        零个或多个不包含初始化数据的数据段，数据段的属性为可读写。

# 2410设计
## 总体知识：
### 阐述CPU、外设、外设控制器、时序、寄存器的相互关系？

#### Cpu如何控制外设？

#### 有外设控制器与无外设控制器CPU对外设的编程控制有何异同？

### 寄存器编程的本质？如何获取寄存器的配置？

## 2410：
### 2410核心电路设计？（晶振选择、启动选择、数据宽度）

### 2410nor和nand启动过程分析？

### S3C2410的中断处理流程？

### S3C2410的串口、外部中断、AD等寄存器的编程能力（会读datasheet、会编程、会分析相关代码）

### 时钟、看门狗的相关概念，pwm占空比

### 关于时序：重点串口、I2c、spi；要求看图反推出数据，或有数据画出波形，会模拟时序编程

### 相关数据手册时序图与寄存器配置之间关系：重点LCD控制器时序、存储控制器时序、串口时序

### 重点掌握：读手册、寄存器编程、时序分析、时序编程


# VIVI
## 什么是bootloader、 Bootloader在系统中的位置、 Bootloader功能、 Bootloader操作模式 、 Bootloader启动过程
## 相关启动代码分析

# uCos-II
## 基本概念
### 可重入函数的概念，能够识别代码是否有可重入性
### 剥夺型与不可剥夺型内核
### 进程上下文
### uCos-II的任务切换
### 临界区的概念
### 实时系统的概念
## uCos-II内核的相关知识
### 初始化、启动
### 任务组成、状态、任务的调度、任务的切换、优先级管理、中断退出
### 时间管理内核代码分析
### 移植代码分析:
### 执行uCos-II初始化后系统内核的主要数据结构？
### 简述任务的创建过程？

##  Task scheduler
    void OS_Sched (void)    /*os_core.c中*/
    {
        INT8U y;
        OS_ENTER_CRITICAL(); 
        if ((OSLockNesting =0)&&(OSIntNesting= 0)) {	
            y = OSUnMapTbl[OSRdyGrp];获得最高优先级的高三位	
                        OSPrioHighRdy = (INT8U)((y << 3) + OSUnMapTbl[OSRdyTbl[y]]) 
            if (OSPrioHighRdy != OSPrioCur) {	
                OSTCBHighRdy=OSTCBPrioTbl[OSPrioHighRdy];
                OSCtxSwCtr++;	
                OS_TASK_SW();	
            }
        }
        OS_EXIT_CRITICAL();
    }
    全局变量OSIntNesting判断是否还有中断
    全局变量OSLockNesting判断是否给调度器上锁
## 任务切换OS_TASK_SW()的示意性代码
    OS_CPU.H
    #define  OS_TASK_SW()         OSCtxSw()

    Void OSCtxSw(void)
    {
        将R1,R2,R3及R4推入当前堆栈；
        OSTCBCurOSTCBStkPtr = SP;
        OSTCBCur              = OSTCBHighRdy;
        SP                    = OSTCBHighRdy OSTCBSTKPtr;
        将R4,R3,R2及R1从新堆栈中弹出；
        执行中断返回指令；
    }
#
    ;	void OS_TASK_SW(void)     /任务：保存当前任务上下文，装入新任务上下文 /
    ;	
    ;	Perform a context switch.
    ;
    ;	On entry, OSTCBCur and OSPrioCur hold the current TCB and priority
    ;	and OSTCBHighRdy and OSPrioHighRdy contain the same for the task
    ;	to be switched to.

    OS_TASK_SW
        STMFD	sp!, {lr}		; save pc
        STMFD	sp!, {lr}		; save lr
        STMFD	sp!, {r0-r12}		; save registers and ret address
        MRS		r4, CPSR
        STMFD	sp!, {r4}		; save current PSR
        MRS		r4, SPSR	
        STMFD	sp!, {r4}		; save SPSR

        ; OSPrioCur = OSPrioHighRdy
        LDR	r4, addr_OSPrioCur
        LDR	r5, addr_OSPrioHighRdy
        LDRB	r6, [r5]              ;优先级仅为一个字节
        STRB	r6, [r4]
        
        ; Get current task TCB address
        LDR	r4, addr_OSTCBCur
        LDR	r5, [r4]
        STR	sp, [r5]		; store sp in preempted tasks's TCB


        ; Get highest priority task TCB address
        LDR	r6, addr_OSTCBHighRdy
        LDR	r6, [r6]
        LDR	sp, [r6]		; get new task's stack pointer

        ; OSTCBCur = OSTCBHighRdy
        STR	r6, [r4]		; set new current task TCB address

    ; restore task's mode regsiters
        LDMFD	sp!, {r4}
        MSR	SPSR, r4
        LDMFD	sp!, {r4}
        MSR	CPSR, r4

    ; return in new task context
        LDMFD	sp!, {r0-r12, lr, pc}
