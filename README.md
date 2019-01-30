package testBrowser;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;


public class FreeCRM {

	WebDriver driver; //creating object for webDriver interface so that the abstract methods of webDriver can be invoked
	public void invokeBrowserandURL(){
		System.setProperty("webdriver.chrome.driver","C:\\Users\\*****\\Downloads\\chromedriver_win32\\chromedriver.exe");
		driver=new ChromeDriver();
		System.out.println("browser is opened");
		driver.get("https://www.freecrm.com");
		System.out.println("URL is opened");
	}
	
	public void getURLTitle()
	{
		driver.getCurrentUrl();	     //this method fetches the URL of the webpage opened
	     String actualTitle = driver.getTitle(); //this method retrieves title of opened web page and stores in a variable 'actualTitle'
	     System.out.println(actualTitle);        // print the webpage title stored in actualTitle
	     
	}
	
	public void signUp(){
		
		System.out.println("SignUp process starts");
        //driver.findElement(By.linkText("https://www.freecrm.com/register/")).click();
        driver.findElement(By.xpath("//*[@id='navbar-collapse']/ul/li[2]/a")).click();
        
        //FirstName is a webElement variable declared to store the path of 'FirstName' web element
		WebElement FirstName = driver.findElement(By.cssSelector("#multipleForm > div:nth-child(4) > input"));
    
    //sendkeys() is the abstract method implemented to pass the value to the webelement in webpage
		FirstName.sendKeys("testUser");
    
		WebElement LastName = driver.findElement(By.cssSelector("#multipleForm > div:nth-child(5) > input"));
		LastName.sendKeys("new");
		WebElement Email=driver.findElement(By.xpath("//*[@id='multipleForm']/div[5]/input"));
		Email.sendKeys("testusernew@mail.com");
        WebElement ConfirmEmail=driver.findElement(By.xpath("//*[@id='multipleForm']/div[6]/input"));
        ConfirmEmail.sendKeys("testusernew@mail.com");
        WebElement username=driver.findElement(By.name("username"));
        username.sendKeys("tu01");
        WebElement password=driver.findElement(By.name("password"));
        password.sendKeys("pwd123");
        WebElement confirmPassword=driver.findElement(By.name("passwordconfirm"));
        confirmPassword.sendKeys("pwd123");
       driver.findElement(By.xpath("//*[@id='multipleForm']/div[11]/div/label/input")).click();
       driver.findElement(By.id("submitButton")).click();
       System.out.println("SignUp process ends");
	}

	public void closeBrowser() {
       driver.quit();
       System.out.println("browser is closed");
	}
	
	
	public static void main(String[] args) {
		
		FreeCRM freeCRM=new FreeCRM();
		freeCRM.invokeBrowserandURL();
		freeCRM.getURLTitle();
		freeCRM.signUp();
		freeCRM.closeBrowser();
	}
	
}
