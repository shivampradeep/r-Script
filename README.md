# r-Script
# Basic commands in R
data_manish = read.csv('C://Users//shivam//Desktop//R session//Titanic_DataSet.csv', header= TRUE)
attach(data_manish)
tbl_Titanic_data <- tbl_df(data_manish)



summary(data_manish)
glimpse(data_manish)

titanic_subset<-filter(data_manish, Sex == 'male')
View(titanic_subset)
gender<- group_by(data_manish, Sex)
avg_age <- summarise(gender,avg_age=mean(Age,na.rm = TRUE))

tbl_Titanic_data %>% 
  group_by(Sex) %>% 
  summarise(avg_age=mean(Age,na.rm = TRUE)) %>% 
  arrange(avg_age)

arrange(tbl_Titanic_data, desc(Fare))

agg<-group_by(tbl_Titanic_data,Pclass,SibSp,Cabin)
freqs<-summarise(agg,n())

subset_pclass <-filter(tbl_Titanic_data,Pclass==1)
select=distinct(select(tbl_Titanic_data,Pclass))

?mutate

mutated_select <- mutate(select, pclass_new = Pclass + 1)
names(mutated_select)
transmute(select, pclass_new= Pclass+1)

a<-tbl_df(data.frame(x1=c(1,2,3),x2=c('Shivam','Murli','Mudit')))
b<-tbl_df(data.frame(x1=c(1,2,4),x3=c('Ananya','Nitin','Sandeep')))
#performing a left join b
left_join(a,b,by="x1")
#performing a right join b
right_join(a,b,by="x1")
#performing a inner join b
inner_join(a,b,by="x1")
#performing a full join b
full_join(a,b,by="x1")
#performing a semi join b
semi_join(a,b,by="x1")
#performing a anti join b
anti_join(a,b,by="x1")

filter(data_manish,is.na(Age)==TRUE)


