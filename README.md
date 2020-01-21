# NGO-application-using-tkinter
This is just a small application using tkinter where canvas is used to create a page and many more. this is just a small example to use tkinter to create some difference.

import sqlite3
import tkinter
import webbrowser
from webbrowser import *
from tkinter import *
from tkinter import messagebox
a=Tk()
a.title("NGO")

def ask():
    t = Toplevel()
    c=Canvas(t,height=950,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")

    Fullname=StringVar()
    Email=StringVar()
    var=IntVar()
    cont=StringVar()
    var1=IntVar()
    

        
    
    def registration_form():
        def database():
            name1=Fullname.get()
            email=Email.get()
            contact=cont.get()
            gender=var.get()
            address=var1.get()
            
            conn=sqlite3.connect('Register.db')
            with conn:
                cursor=conn.cursor()
            cursor.execute('CREATE TABLE IF NOT EXISTS Registration(Fullname TEXT,Email TEXT,Contact INT,Gender TEXT,Address TEXT)')
            cursor.execute('INSERT INTO Registration(FullName,Email,Contact,Gender,Address)VALUES(?,?,?,?,?)',(name1,email,contact,gender,address))
            conn.commit()
            #conn.close()

        
        def successful():
            messagebox.showinfo("Registered sucessfully.")

        t.title("Registration Form")

       
        label_0 = Label(c, text="Register Yourself !",width=20,font=("Times New Roman bold", 20),bg="light blue",fg="white")
        label_0.place(x=270,y=53)


        label_1 = Label(c, text="Full Name",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
        label_1.place(x=80,y=130)

        entry_1 = Entry(c,width=50)
        entry_1.place(x=280,y=130)

        label_2 = Label(c, text="Email-id",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
        label_2.place(x=80,y=180)

        entry_2 = Entry(c,width=50)
        entry_2.place(x=280,y=180)

        label_3 = Label(c, text="Contact Number",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
        label_3.place(x=80,y=230)

        entry_3 = Entry(c,width=50)
        entry_3.place(x=280,y=230)

        label_4 = Label(c, text="Gender",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
        label_4.place(x=80,y=280)
    

        selected=IntVar()
        r1=Radiobutton(c, text="Male",value=1,height=2,width=10,font=('bold',10),bg="light blue",variable=selected)
        r2=Radiobutton(c, text="Female",value=2,height=2,width=10,font=('bold',10),bg="light blue",variable=selected)

        def clicked():
            print(selected.get())

        r1.place(x=280,y=260)    
        r2.place(x=390,y=260)
     
        label_5 = Label(c, text="Address",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
        label_5.place(x=80,y=330)

        entry_5 = Text(c,width=38,height=3.3)
        entry_5.place(x=280,y=330)
        

        Button(c, text='Submit',font=("Georgia bold",12),width=8,bg='red',fg='white',relief='raised',command=database).place(x=370,y=480)

    c.create_rectangle(5,710,950,790,fill="pink",outline="blue",width=2)

    label_1 = Label(c,text="Call Us: +91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=150,y=730)

    label_1 = Label(c,text="Mail Us: yogibawankule22@gmail.com",width=28,font=("Times New Roman bold",12),bg="pink",fg="black")
    label_1.place(x=450,y=730)
 
    Button(c,text='Home',font=("Georgia bold",8),width=9,bg='light grey',fg='black',relief='ridge').place(x=100,y=760)

    Button(c,text='About Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=About).place(x=210,y=760)

    Button(c,text='Our Work',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=ourwork).place(x=330,y=760)

    Button(c,text='Get Involved',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=Internship_form).place(x=450,y=760)

    Button(c,text='Contact Us',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=570,y=760)

    Button(c,text='Donate',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=690,y=760)

        
    c.pack()
    registration_form()
    t.mainloop()
    
def Contact_Us():
    cont=Toplevel()
    c=Canvas(cont,height=850,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")


    def successful():
        messagebox.showinfo("Thank You !")

    cont.title("Contact_Us")
    
    label_0 = Label(cont, text="Get in touch with us !",width=20,font=("Times New Roman bold", 20),bg="light blue",fg="white")
    label_0.place(x=600,y=53)


    label_1 = Label(cont, text="Full Name",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_1.place(x=430,y=150)

    entry_1 = Entry(cont,width=40)
    entry_1.place(x=650,y=150)

    label_2 = Label(cont, text="Email-id",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_2.place(x=425,y=200)

    entry_2 = Entry(cont,width=40)
    entry_2.place(x=650,y=200)

    label_3 = Label(cont, text="Contact Number",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_3.place(x=420,y=250)

    entry_3 = Entry(cont,width=40)
    entry_3.place(x=650,y=250)

    label_5 = Label(cont, text="Drop a Message For Us !",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_5.place(x=650,y=300)

    entry_5 = Text(cont,width=30,height=6)
    entry_5.place(x=650,y=350)

    
    Button(cont, text='Submit',font=("Georgia bold",12),width=8,bg='red',fg='white',relief='raised',command=successful).place(x=697,y=480)

    c.create_rectangle(5,710,950,790,fill="pink",outline="blue",width=2)

    label_1 = Label(c,text="Call Us: +91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=125,y=730)

    label_2 = Label(c,text="Mail Us: yogibawankule22@gmail.com",width=28,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_2.place(x=350,y=730)
 
    Button(c,text='Home',font=("Georgia bold",8),width=9,bg='light grey',fg='black',relief='ridge').place(x=150,y=760)

    Button(c,text='About Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=About).place(x=285,y=760)

    Button(c,text='Our Work',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=ourwork).place(x=420,y=760)

    Button(c,text='Get Involved',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=Internship_form).place(x=565,y=760)

    Button(c,text='Donate',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Donate_Now).place(x=710,y=760)
    
    c.pack()
    cont.mainloop()



Fullname=StringVar()
Email=StringVar()
var=IntVar()
cont=StringVar()
var1=IntVar()

def database():
    name1=Fullname.get()
    email=Email.get()
    contact=cont.get()
    gender=var.get()
    address=var1.get()

    conn=sqlite3.connect('Form3.db')
    with conn:
        cursor=conn.cursor()
    cursor.execute('CREATE TABLE IF NOT EXISTS Internship_form(Fullname TEXT,Email TEXT,Contact INT,Gender TEXT,Address TEXT)')
    cursor.execute('INSERT INTO Internship_form(FullName,Email,Contact,Gender,Address)VALUES(?,?,?,?,?)',(name1,email,contact,gender,address))
    conn.commit()



def Internship_form():
    t = Toplevel()
    c=Canvas(t,height=950,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")

    def successful():
        messagebox.showinfo("Registered sucessfully")

    t.title("Internship Form")
           
    label_0 = Label(c, text="Be A Part of Change !",width=20,font=("Times New Roman bold", 20),bg="light blue",fg="white")
    label_0.place(x=250,y=53)


    label_1 = Label(c, text="Full Name",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_1.place(x=100,y=130)

    entry_1 = Entry(c,width=40)
    entry_1.place(x=280,y=130)

    label_2 = Label(c, text="Email-id",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_2.place(x=100,y=180)

    entry_2 = Entry(c,width=40)
    entry_2.place(x=280,y=180)

    label_3 = Label(c, text="Contact Number",width=18,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_3.place(x=80,y=230)

    entry_3 = Entry(c,width=40)
    entry_3.place(x=280,y=230)

    label_4 = Label(c, text="Gender",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_4.place(x=100,y=280)
    
    selected=IntVar() 
    r1=Radiobutton(c, text="Male",value=1,height=2,width=10,font=('bold',10),bg="light blue")
    r2=Radiobutton(c, text="Female",value=2,width=10,font=('bold',10),bg="light blue")

    def clicked():
        print(selected.get()) 
    
    r1.place(x=280,y=270)
    r2.place(x=360,y=280)
    
    label_5 = Label(c, text="Address",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_5.place(x=100,y=330)

    entry_5 = Text(c,width=30,height=5)
    entry_5.place(x=280,y=330)


    label_5 = Label(c, text="Internship",width=17,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_5.place(x=90,y=470)
   

    Checkbutton(c, text="Full Time",onvalue=1,offvalue=0,height=2,width=35,font=('bold',10),bg="light blue").place(x=230,y=450)
    Checkbutton(c, text="Part Time",onvalue=1,offvalue=0,height=2,width=35,font=('bold',10),bg="light blue").place(x=230,y=480)


    Button(c, text='Submit',font=("Georgia bold",12),width=8,bg='red',fg='white',relief='raised',command=database).place(x=350,y=550)

    c.create_rectangle(5,710,950,790,fill="pink",outline="blue",width=2)

    label_1 = Label(c,text="Call Us: +91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=125,y=730)

    label_1 = Label(c,text="Mail Us: yogibawankule22@gmail.com",width=28,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=350,y=730)
 
    Button(c,text='Home',font=("Georgia bold",8),width=9,bg='light grey',fg='black',relief='ridge').place(x=150,y=760)

    Button(c,text='About Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=About).place(x=285,y=760)

    Button(c,text='Our Work',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=ourwork).place(x=420,y=760)

    Button(c,text='Contact Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=565,y=760)

    Button(c,text='Donate',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Donate_Now).place(x=710,y=760)

        
    c.pack()
    t.mainloop()

    
def ourwork():
    ow=Toplevel()
    ow.title("Our Work")

    c=Canvas(ow,height=950,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")

    label_1 = Label(c,text="OUR WORK ",width=20,font=("Times New Roman bold",20),bg="light blue",fg="White")
    label_1.place(x=300,y=50)


    p1=PhotoImage(file="p1.png")    
    c.create_image(135,440,image=p1)

    p2=PhotoImage(file="p3.png")    
    c.create_image(450,200,image=p2)

    p3=PhotoImage(file="p4.png")    
    c.create_image(770,650,image=p3)

    p4=PhotoImage(file="p6.png")    
    c.create_image(135,200,image=p4)

    p5=PhotoImage(file="p8.png")    
    c.create_image(140,680,image=p5)

    p6=PhotoImage(file="p9.png")    
    c.create_image(790,200,image=p6)

    p7=PhotoImage(file="p7.png")    
    c.create_image(450,400,image=p7)

    p10=PhotoImage(file="p10.png")    
    c.create_image(430,660,image=p10)

    p11=PhotoImage(file="p11.png")    
    c.create_image(790,400,image=p11)

    c.pack()
    ow.mainloop()

def About():
    t1=Tk()
    t1.title("About Us")
    c=Canvas(t1,height=950,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")
    label_0 = Label(c, text="About Us",width=20,font=("Times New Roman bold", 20),bg="light blue",fg="white")
    label_0.place(x=270,y=53)

    f=open("Aboutus.txt",'r')
    text1=f.read()
    text2=str(text1)
    t=text2.lstrip()
    Label(c,text=t,bg="light blue",width=70,height=20,font=("Times New Roman",14)).place(x=100,y=100)
    f.close()
    c.create_rectangle(5,710,950,790,fill="pink",outline="blue",width=2)

    label_1 = Label(c,text="Call Us: +91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=150,y=730)

    label_1 = Label(c,text="Mail Us: yogibawankule22@gmail.com",width=28,font=("Times New Roman bold",12),bg="pink",fg="black")
    label_1.place(x=450,y=730)
 
    Button(c,text='Home',font=("Georgia bold",8),width=9,bg='light grey',fg='black',relief='ridge').place(x=100,y=760)

    Button(c,text='About Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=About).place(x=210,y=760)

    Button(c,text='Our Work',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=ourwork).place(x=330,y=760)

    Button(c,text='Get Involved',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=Internship_form).place(x=450,y=760)

    Button(c,text='Contact Us',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=570,y=760)

    Button(c,text='Donate',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=690,y=760)

    c.pack()
    t1.mainloop()


def Donate_Now():
    dt=Toplevel()
    c=Canvas(dt,height=850,width=950,background="light blue",highlightthickness=3,highlightbackground="blue")
    c.place(x=20,y=80)

    
    def successful():
            messagebox.showinfo("Thank You For Your Help !")

    dt.title("Donate_Now")
    
    label_0 = Label(dt, text="Gift Your Hand's to Needy One!",width=30,font=("Times New Roman bold", 20),bg="light blue",fg="white")
    label_0.place(x=600,y=53)


    label_1 = Label(dt, text="Full Name",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_1.place(x=430,y=150)

    entry_1 = Entry(dt,width=40)
    entry_1.place(x=650,y=150)

    label_2 = Label(dt, text="Email-id",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_2.place(x=425,y=200)

    entry_2 = Entry(dt,width=40)
    entry_2.place(x=650,y=200)

    label_3 = Label(dt, text="Contact Number",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_3.place(x=420,y=250)

    entry_3 = Entry(dt,width=40)
    entry_3.place(x=650,y=250)

    label_4 = Label(dt, text="Amount",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_4.place(x=420,y=300)

    entry_4 = Entry(dt)
    entry_4.place(x=650,y=300)
    

    label_5 = Label(dt, text="Drop a Message For Us !",width=20,font=("Georgia bold", 12),bg="light blue",fg="black")
    label_5.place(x=650,y=340)

    entry_5 = Text(dt,width=30,height=5)
    entry_5.place(x=650,y=370)


    Button(dt, text='Donate',font=("Georgia bold",12),width=8,bg='red',fg='white',relief='raised',command=successful).place(x=697,y=530)

    c.create_rectangle(5,710,950,790,fill="pink",outline="blue",width=2)

    label_1 = Label(c,text="Call Us: +91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=125,y=730)

    label_1 = Label(c,text="Mail Us: yogibawankule22@gmail.com",width=28,font=("Times New Roman bold",11),bg="pink",fg="black")
    label_1.place(x=350,y=730)
 
    Button(c,text='Home',font=("Georgia bold",8),width=9,bg='light grey',fg='black',relief='ridge').place(x=150,y=760)

    Button(c,text='About Us',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=About).place(x=285,y=760)

    Button(c,text='Our Work',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=ourwork).place(x=420,y=760)

    Button(c,text='Get Involved',font=("Georgia bold",8),width=10,bg='light grey',fg='black',relief='ridge',command=Internship_form).place(x=565,y=760)

    Button(c,text='Contact Us',font=("Georgia bold",8),width=11,bg='light grey',fg='black',relief='ridge',command=Contact_Us).place(x=710,y=760)


    c.pack()
    dt.mainloop()  




    
c=Canvas(a,height=950,width=950,background="pink",highlightthickness=3,highlightbackground="blue")
c.place(x=20,y=900)
i1=PhotoImage(file="img.png")
c.create_image(300,300,image=i1)
    
Button(c,text='Home',font=("Georgia bold",9),width=8,bg='light grey',fg='black',relief='raised',border=8).place(x=30,y=100)

Button(c,text='About Us',font=("Georgia bold",9),width=10,bg='light grey',fg='black',relief='raised',border=8,command=About).place(x=135,y=100)

Button(c,text='Our Work',font=("Georgia bold",9),width=10,bg='light grey',fg='black',relief='raised',border=8,command=ourwork).place(x=255,y=100)

Button(c,text='Get Involved',font=("Georgia bold",9),width=11,bg='light grey',fg='black',relief='raised',border=8,command=Internship_form).place(x=375,y=100)

Button(c,text='Contact Us',font=("Georgia bold",9),width=10,bg='light grey',fg='black',relief='raised',border=8,command=Contact_Us).place(x=500,y=100)

Button(c,text='Donate',font=("Georgia bold",9),width=10,bg='light grey',fg='black',relief='raised',border=7,command=Donate_Now).place(x=615,y=100)

Button(c,text='Facebook',font=("Georgia bold",9),width=9,bg='white',fg='black',relief='sunken',border=6).place(x=850,y=200)

Button(c,text='Instagram',font=("Georgia bold",9),width=9,bg='white',fg='black',relief='sunken',border=6).place(x=850,y=250)

Button(c,text='Twitter',font=("Georgia bold",9),width=9,bg='white',fg='black',relief='sunken',border=6).place(x=850,y=300)

label_1 = Label(c,text="yogibawankule22@gmail.com",width=23,font=("Times New Roman bold",11),bg="pink",fg="black")
label_1.place(x=730,y=23)

label_2 = Label(c,text="Call Us :+91-9096360963",width=24,font=("Times New Roman bold",11),bg="pink",fg="black")
label_2.place(x=730,y=49)


Button(c,text='Register For Change',font=("Georgia bold",12),width=16,bg='white',border=6,fg='black',relief='sunken',command=ask).place(x=200,y=650)

c.pack()
a.mainloop()


        
    


            

       
