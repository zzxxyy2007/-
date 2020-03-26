#!/usr/bin/env python
#上面的东西不能删
import wx
import time 

class HelloFrame(wx.Frame):

    def __init__(self, *args, **kw):
        super(HelloFrame, self).__init__(*args, **kw)

        pnl = wx.Panel(self)

        st = wx.StaticText(pnl, label='我不知道该说什么')
        font = st.GetFont()
        font.PointSize += 5
        font = font.Bold()
        st.SetFont(font)

        sizer = wx.BoxSizer(wx.VERTICAL)
        sizer.Add(st, wx.SizerFlags().Border(wx.TOP|wx.LEFT, 25))
        pnl.SetSizer(sizer)

        self.makeMenuBar()

        self.CreateStatusBar()
        self.SetStatusText("周昕扬制作")


    def makeMenuBar(self):
        
        fileMenu = wx.Menu()
        
        ZXItem = fileMenu.Append(-1,"&致谢",
                                 "致谢人员")

        tistItem = fileMenu.Append(-1,"&打开瞧瞧吧",
                                 "嘻嘻")
        
        helloItem = fileMenu.Append(-1, "&通知",
                "就是告诉你干什么事")
        fileMenu.AppendSeparator()

        exitItem = fileMenu.Append(wx.ID_EXIT)

        helpMenu = wx.Menu()
        aboutItem = helpMenu.Append(wx.ID_ABOUT)

        menuBar = wx.MenuBar()
        menuBar.Append(fileMenu, "&菜单")
        menuBar.Append(helpMenu, "&帮助")

        self.SetMenuBar(menuBar)

        self.Bind(wx.EVT_MENU, self.OnHello, helloItem)
        self.Bind(wx.EVT_MENU, self.OnExit,  exitItem)
        self.Bind(wx.EVT_MENU, self.OnAbout, aboutItem)
        self.Bind(wx.EVT_MENU, self.Ontist, tistItem)
        self.Bind(wx.EVT_MENU, self.OnZX, ZXItem)

    def OnZX(self,event):
        
        wx.MessageBox('''感谢
        Python
        wxPthon
        周昕扬
        (就我一个人做的，上面两个是语言与库)''')
    
    def Ontist(self,event):
        
        wx.MessageBox('''武汉加油，中国加油，世界加油！来自2020年3月25日，蝙蝠时代。周昕扬''',
                      "加油",
                       wx.OK|wx.ICON_INFORMATION)
    
    def OnExit(self, event):

        self.Close(True)


    def OnHello(self, event):

        wx.MessageBox("菜单里很简洁，不是吗？",
                      '菜单',
                      wx.OK|wx.ICON_INFORMATION)


    def OnAbout(self, event):

        wx.MessageBox("帮助里啥也没有，别看了",
                      "帮助",
                      wx.OK|wx.ICON_INFORMATION)

if __name__ == '__main__':

    app = wx.App()
    frm = HelloFrame(None, title='周昕扬的应用程序')
    frm.Show()
    app.MainLoop()
